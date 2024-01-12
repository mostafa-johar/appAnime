<script setup>
const pros = defineProps(['anime'])
</script>

<template>
     <div class="card mb-2 rounded-lg shadow-lg overflow-hidden md:hover:scale-125 transition">
          <a :href="anime.url" class="block" target="_blank">
               <img :src="anime.images.webp.image_url" class="w-full h-[300px] object-cover " alt="anime" loading="lazy"/>
          </a>
          <h3 class="p-2 font-light"> {{ anime.title }}</h3>

     </div>
</template>
