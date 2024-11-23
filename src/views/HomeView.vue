<template>
    <div class="home">
        <div class="posts">
            <div class="post" v-for="post in posts" :key="post.id">
                <div class="post-header">
                    <a class="post-logo" href="#">
                    <img src="res/images/pfp.jpg" width="50" height="50" alt="My pfp" />
                    </a>
                    <p>{{ post.date }}</p>
                </div>
                <div class="post-content">
                    <img v-if="post.image" class="post-photo" :src="post.image" alt="Post image" />
                    <p>{{ post.content }}</p>
                </div>
                <div class="post-footer">
                    <img class="like" src="res/images/Facebook_logo_thumbs_up_like_transparent_SVG.svg" alt="Like icon"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Home",
    data() {
        return {
            posts: [],
        };
    },
    methods: {
        async fetchPosts() {
            try {
                const response = await fetch(posts.json);
                const data = await response.json();
                this.posts = data.record || data;

                const postsContainer = document.querySelector('.posts');
                postsContainer.innerHTML = '';


                posts.forEach(post => {
                    const postElement = document.createElement('div');
                    postElement.classList.add('post');


                    const postHeader = document.createElement('div');
                    postHeader.classList.add('post-header');
                    postHeader.innerHTML = `
                        <a class="post-logo" href="#"><img src="res/images/pfp.jpg" width="50" height="50" alt="My pfp"></a>
                        <p>${post.date}</p>
                    `;


                    const postContent = document.createElement('div');
                    postContent.classList.add('post-content');
                    if (post.image) {
                        postContent.innerHTML = `<img class="post-photo" src="${post.image}" alt="Post image">`;
                    }
                    postContent.innerHTML += `<p>${post.content}</p>`;


                    const postFooter = document.createElement('div');
                    postFooter.classList.add('post-footer');
                    postFooter.innerHTML = `
                        <img class="like" src="res/images/Facebook_logo_thumbs_up_like_transparent_SVG.svg" alt="Like icon">
                    `;


                    postElement.appendChild(postHeader);
                    postElement.appendChild(postContent);
                    postElement.appendChild(postFooter);
                    postsContainer.appendChild(postElement);
                }
            } catch (error) {
                console.error("Error fetching posts: ", error);
            }
        },
    },
    created() {
        this.fetchPosts();
    },
};
</script>