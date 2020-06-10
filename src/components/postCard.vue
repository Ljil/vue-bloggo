<template>
    <div class="post_card">
        <router-link :to="{ name: 'Detail', params: {slug: post.slug}}">
            <h1>{{ post.title }}</h1>
        </router-link>
        <p>{{ post.description }}</p>
        <p>
            <span class="tags" :key="tag.id" v-for="tag in post.tags">{{ tag.title }}</span>
        </p>
    </div>
</template>

<script>
    export default {
        name: "postCard",
        props: {
            post: Object,
        }
    }
</script>

<style scoped>
    .tags {
        margin: 0 0.5rem;
        padding: 2px 10px;
        border-radius: 5px;
        background-color: coral;
        font-size: small;
        font-weight: bolder;
        box-shadow: -2px 2px 3px lightcoral;
    }
    .post_card {
        margin: 2rem 5rem;
        box-shadow: 5px 10px 3px #2c3e50;
        border: aqua 2px solid;
        border-radius: 1rem;
    }
    .post_card p {
        flex-wrap: wrap;
    }
</style>