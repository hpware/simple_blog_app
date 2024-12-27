<script setup lang="ts">
const formatDate = (dateString: string) => {
    const D1 = { year: "numeric", month: "long", day: "numeric" };
    return new Date(dateString).toLocaleDateString("zh-TW", D1);
};
</script>
<template>
    <div>
        <ContentDoc>
            <template v-slot="{ doc }">
                <article>
                    <h1>{{ doc.title }}</h1>
                    <div class="meta">
                        <span>{{ formatDate(doc.date) }}</span>
                    </div>
                    <ContentRenderer :value="doc" />
                </article>
            </template>
            <template #not-found>
                <h1></h1>
            </template>
        </ContentDoc>
    </div>
</template>
