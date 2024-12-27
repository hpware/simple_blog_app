<script setup lang="ts">
const fdate = (dateString: string) => {
    const D1 = { year: "numeric", month: "long", day: "numeric" };
    return new Date(dateString).toLocaleDateString("zh-TW", D1);
};
</script>
<template>
    <div>
        <h1>Blog</h1>
        <ContentList path="/post/">
            <template #default="{ list }">
                <div v-for="article in list" :key="article._path">
                    <NuxtLink :to="article._path" class="card">
                        <div>
                            <div>
                                <h2>{{ article.title }}</h2>
                                <span>{{ fdate(article.date) }}</span>
                            </div>
                            <p>{{ article.description }}</p>
                        </div>
                    </NuxtLink>
                </div>
            </template>
            <template #not-found>
                <p>No post</p>
            </template>
        </ContentList>
    </div>
</template>
