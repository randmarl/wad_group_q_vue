<template>
    <div class="post">
        <div class="post-header">
            <a class="post-logo" href="#">
                <img :src="profileImage" width="50" height="50" alt="User pfp" />
            </a>
            <p>{{ post.date }}</p>
        </div>
        <div class="post-content">
            <img v-if="post.image" class="post-photo" :src="post.image" alt="Post image" />
            <p>{{ post.content }}</p>
        </div>
        <div class="post-footer">
            <p class="like"> 👍 </p>
        </div>
    </div>
</template>
<script>
import userProgileImage from '@/assets/pfp.jpg'

export default {
    name: "PostObject",
    props: {
        post: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            profileImage: userProgileImage
        };
    },
    mounted() {
        if (this.post.image) {
            console.log('Image URL: ', this.post.image);
        }
    }
};
</script>

<style>
.post {
    background-color: rgb(209, 209, 209);
    border-radius: 10px;
    margin: 10px;
}
.post-header {
    flex-direction: row;
    justify-content: space-between;
    display: flex;
    align-items: center;
    border-radius: 10px;
    margin: 10px;
}
.post-footer {
    justify-content: left;
}
.post-content {
    justify-content: center;
    margin: 5px;
}
.post-photo {
    width: 100%;
    border-radius: 5px;
}
.like {
    border-radius: 5px;
}
</style>