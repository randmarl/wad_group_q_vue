<template>
    <div class="content">
        <PostObject v-for="post in posts" :key="post.id" :post="post"/>
    </div>
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
                this.posts = Data.record || Data;
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