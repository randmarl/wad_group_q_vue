<template>
    <div id="home">
      <div class="sidepanel"></div>
      <div class="content">
        <PostObject v-for="post in posts" :key="post.id" :post="post" @update-likes="updateLikes" />
        <button class="reset-button" v-on:click="resetLikes"> Reset Likes </button>
      </div>
      <div class="sidepanel"></div>
    </div>
  </template>
  
  <script>
  import PostObject from "../components/Post.vue";
  import { mapState, mapActions } from 'vuex';
  
  export default {
    name: "HomeView",
    components: {
      PostObject,
    },
    computed: {
      ...mapState({
        posts: state => state.posts, // Get posts from Vuex store
      }),
    },
    methods: {
      ...mapActions({
        resetLikes: 'resetLikes', // Map Vuex resetLikes action
        updateLikes: 'incrementLikes', // Map Vuex incrementLikes action
      }),
    },
  };
  </script>
  
<style>
  #home {
  display: flex;
  flex-direction: row;
  justify-content: space-between; /* Distribute space between content and side panels */
  width: 100%;
  height: 100%;
  margin-bottom: 40px;
}

.content {
  background-color: white;
  max-width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start; /* Align posts from the top */
  overflow-y: auto;
}

.side-panel {
  flex: 1; /* Side panels take up less space */
  background-color: rgb(209, 209, 209);
}

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
  