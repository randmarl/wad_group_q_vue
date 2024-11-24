<template>
    <div class="content">
        <PostObject v-for="post in posts" :key="post.id + '-' + post.likes" :post="post" @reset-likes="resetLikesForAll"/>
    </div>
    <button class="reset-button" v-on:click="resetLikes"> Reset Likes </button>
</template>

<script>
import PostObject from "../components/Post.vue";
import Data from '@/assets/posts.json';

export default {
    name: "HomeView",
    components: {
        PostObject,
    },
    data() {
        return {
            posts: [],
        };
    },
    methods: {
        async fetchPosts() {
            try {
                //const response = await fetch(Data);
                //const data = await response.json();
                //this.posts = data.record || data;
                this.posts = (Data.record || Data).map(post => {
                    return {
                        ...post,
                        likes: post.likes || 0,
                    };
                });
            } catch (error) {
                console.error("Error fetching posts: ", error);
            }
        },
        resetLikes() {
            this.posts.forEach((post) => {
                post.likes = 0;
            });
        },
        resetLikesForAll(postId) {
            const post = this.posts.find((p) => p.id === postId);
            if (post) {
                post.likes = 0;
            }
        }
    },
    mounted() {
        this.fetchPosts();
    },
};
</script>

<style>
.reset-button {
  margin: 20px 0;
  padding: 10px 20px;
  font-size: 16px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.reset-button:hover {
  background-color: #36a372;
}
</style>