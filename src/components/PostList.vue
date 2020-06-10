<template>
    <div class="list_container">
        <postCard :key="post.id" v-for="post in posts.results" :post="post"/>
        <hr>
        <Paginator :loadPage="loadPage" :posts="posts"/>
    </div>
</template>

<script>
    import Paginator from "./Paginator";
    import postCard from "./postCard";

    export default {
        name: "PostList",
        components: {
            postCard,
            Paginator,
        },
        data() {
            return {
                posts: {}
            }
        },
        mounted() {
            this.loadPage('http://localhost:8000/api/posts')
        },
        methods: {
            async loadPage(url) {
                this.posts = await fetch(
                    url
                ).then(response => response.json())
            },
        },
    }
</script>

<style scoped>
    a:disabled {
        color: red;
    }
    hr {
        border-color: lightcoral;
        width: 90%;
    }
    .list_container {
        margin-bottom: 5rem;
    }
</style>