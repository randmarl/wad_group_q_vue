<template>
    <div class="post">
        <div class="post-header">
            <a class="post-logo" href="#">
                <img src="res/images/pfp.jpg" width="50" height="50" alt="User pfp" />
            </a>
            <p>{{ post.date }}</p>
        </div>
        <div class="post-content">
            <img v-if="post.image" class="post-photo" :src="post.image" alt="Post image" />
            <p>{{ post.content }}</p>
        </div>
        <div class="post-footer">
            <img class="like" src="res/images/like.svg" alt="Like icon" />
        </div>
    </div>
</template>
<script>
export default {
    name: "PostObject",
    props: {
        post: {
            type: Object,
            required: true,
        },
    },
};
</script>

<style>
post-header {
    flex-direction: row;
    border-radius: 10px;
    margin: 10px;
}
post-footer {
    justify-content: left;
}
post-content {
    justify-content: center;
    margin: 5px;
}
post-photo {
    width: 100%;
    border-radius: 5px;
}
like {
    width: 25px;
    height: 25px;
    margin: 5px;
}
</style>