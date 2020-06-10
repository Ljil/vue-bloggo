<template>
    <div class="post_card">

        <h1>{{ post.title }}</h1>
        <p>
            <span class="tags" :key="tag.id" v-for="tag in post.tags">{{ tag.title }}</span>
        </p>
        <p>{{ post.created }}</p>
        <p>{{ post.text }}</p>
    </div>
</template>

<script>
    export default {
        name: "detailPage",
        props: ['slug'],
        data() {
            return {
                post: {}
            }
        },
        mounted() {
            this.loadPage('http://localhost:8000/api/posts/' + this.slug)
        },
        methods: {
            async loadPage(url) {
                this.post = await fetch(
                    url
                ).then(response => response.json())
            },
        },
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
</style>