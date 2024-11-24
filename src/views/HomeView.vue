<template>
    <div class="content">
        <PostObject v-for="post in posts" :key="post.id" :post="post"/>
    </div>
</template>

<script>
import PostObject from "../components/Post.vue";

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
                const response = await fetch('https://api.jsonbin.io/v3/b/6724d2b8acd3cb34a8a0a39b');
                const data = await response.json();
                this.posts = data.record || data;
            } catch (error) {
                console.error("Error fetching posts: ", error);
            }
        },
    },
    mounted() {
        this.fetchPosts();
    },
};
</script>