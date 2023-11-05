
import type ImagesVue from './Images.vue';


<template>
  <div class="mt-4">
    <div v-if="data.length > 0" class="mb-4">
      About {{ data.length }} results
    </div>
    <div v-for="(item, i) in data" :key="i" class="mb-8">
      <NuxtLink :to="item.href" target="_blank" class="text-blue-700 font-medium ">
        {{ item.title }}
      </NuxtLink>
      <div class="flex mt-4 relative">
        <span class="absolute text-xs text-white bg-gray-600 bg-opacity-60 px-2 rounded-lg bottom-2 left-2 ">{{ item.duration }}</span>
        <img :src="item.images.small" alt="img" class="w-[150px] rounded-lg" />
        <div class="ml-4 ">
          <p class="mb-2 truncate ...">
            {{ item.description }}
          </p>
          <div class="flex mt-4">
            <span class="font-semibold">{{ item.publisher }}</span>
            <span class="mx-1"> - </span>
            <span> {{ item.uploader }}</span>
            <span class="mx-1"> - </span>
            <span>{{ getDate(item.published) }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(['data'])

function getDate (date) {
  const tgl = new Date(date)
  return tgl.toLocaleDateString()
}
</script>