<script setup lang="ts">
const { data: page } = await useAsyncData("werk-page", () => {
  return queryCollection("pages").path("/werk").first();
});
if (!page.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Page not found",
    fatal: true,
  });
}
const { data: cases } = await useAsyncData("werk", () =>
  queryCollection("werk").order("date", "DESC").all()
);
if (!cases.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "werk posts not found",
    fatal: true,
  });
}

useSeoMeta({
  title: page.value?.seo?.title || page.value?.title,
  ogTitle: page.value?.seo?.title || page.value?.title,
  description: page.value?.seo?.description || page.value?.description,
  ogDescription: page.value?.seo?.description || page.value?.description,
});
</script>

<template>
  <div v-if="page">
    <UPageHero
      :title="page.title"
      :description="page.description"
      :links="page.hero.links"
    >
      <template #top>
        <div
          class="absolute rounded-full dark:bg-primary blur-[300px] size-60 sm:size-80 transform -translate-x-1/2 left-1/2 -translate-y-80"
        />

        <LazyStarsBg />
      </template>
    </UPageHero>

    <UPageSection>
      <UPageGrid>
        <UPageCard
          v-for="(work, index) in cases"
          :key="index"
          :title="work.title"
          :description="work.description"
          :image="work.image"
          :to="work.to"
        />
      </UPageGrid>
    </UPageSection>
  </div>
</template>
