<script setup lang="ts">
const userStore = useUserStore();

const title = computed(() => {
  return `Olá${
    userStore.user?.firstName ? `, ${userStore.user.firstName}` : ""
  }, o que vamos aprender hoje?`;
});

const description =
  "Plataforma gratuita de ensino de programação web para pessoas que estão buscando o primeiro emprego na área ou que querem construir seu próprio negócio.";
useSeoMeta({
  title: title,
  description: description,
  ogDescription: description,
  ogImage: "https://menthor.io/brand/menthor-cover.jpg",
});
</script>

<template>
  <div class="px-4 sm:px-8">
    <h1 class="mb-4 text-xl font-bold">
      {{ title }}
    </h1>
    <!-- <div class="mb-6 grid grid-cols-[repeat(auto-fill,_minmax(270px,_1fr))]">
      <RoadMapCard />
      <RoadMapCard />
      <RoadMapCard />
      <RoadMapCard />
    </div>
    <h2 class="mb-4 text-lg font-bold">Recomendados para você</h2> -->
    <div
      class="mb-6 grid grid-cols-[repeat(auto-fill,_minmax(160px,_1fr))] sm:grid-cols-[repeat(auto-fill,_minmax(180px,_1fr))]"
    >
      <ContentNavigation v-slot="{ navigation }">
        <NuxtLink
          v-for="item of navigation"
          :key="item._path"
          :nav-item="item"
          :href="
            item.children && item.children[0].children
              ? item.children[0].children[0]._path
              : ''
          "
        >
          <CourseCard
            :title="item.title"
            :description="item.description"
            :image="item.image"
          />
        </NuxtLink>
      </ContentNavigation>
    </div>
  </div>
</template>
