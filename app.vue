<script setup>

const search_query = ref("")
const animeList = ref([])

const getAnime = async () => {
  const { data } = await $fetch(`https://api.jikan.moe/v4/anime?q=${search_query.value}`)
  animeList.value = data
}

</script>

<template>
  <div class="container mx-auto p-4">

    <header class="flex flex-col justify-center items-center py-12 gap-3">

      <h1 class="text-4xl text-slate-400">The <strong class="text-slate-900">Anime </strong>App</h1>

      <form @submit.prevent="getAnime">
        <input type="search" class="p-2 block md:w-[500px] outline-none shadow-md bg-white text-black"
          placeholder="search..." v-model="search_query">
      </form>

    </header>

    <main>
      <section class="grid lg:grid-cols-5 md:grid-cols-3 sm:grid-cols-2 gap-8" v-if="animeList.length>0">
        <LazyCard v-for="anime in animeList" :key="anime.title" :anime="anime" />
      </section>
      <section v-else>No result, search and <span class="text-pink-700">Click </span>enter...</section>
    </main>

  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;500;600;700&display=swap');

body {
  font-family: 'Lexend', sans-serif;
}
</style>
