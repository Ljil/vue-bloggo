<template>
    <div class="paginator">
            <div>
                <a @click="loadPage(posts.links.previous)" v-if="posts.links.previous">&lt; Предыдущая страница</a>
            </div>
            <div>
                <span>Страница {{ posts.current_page }} из {{ posts.total_pages}}</span>
            </div>
            <div>
                <a @click="loadPage(posts.links.next)" v-if="posts.links.next">Следующая страница&gt;</a>
            </div>
        </div>
</template>

<script>
    export default {
        name: "Paginator",
        props: {
            loadPage: {type: Function},
            posts: Object,
        },
    }
</script>

<style scoped>
    .paginator {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        margin: auto;
    }
    .paginator div {
        vertical-align: center;
    }
</style>