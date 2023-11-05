
<template>
  <div class="mt-4 flex flex-wrap w-full justify-center">
    <div v-for="(item, i) in data" :key="i" class="m-2 h-[250px] p-1 max-w-[200px] ">
      <div class="justify-center flex m-auto">
        <img :src="item.thumbnail" alt="img" class="max-h-[150px] rounded-lg" />
      </div>
      <NuxtLink :to="item.url" target="_blank" class="text-blue-700 font-medium mt-4">
        <p class="mt-2">
          {{ item.title }}
        </p>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(['data'])
</script>