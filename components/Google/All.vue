

<template>
  <div class="mt-4">
    <div class="mb-4">
      About {{ data.length }} results
    </div>
    <div v-for="(item, i) in data" :key="i" class="mb-8">
      <NuxtLink :to="item.href" target="_blank" class="text-blue-700 font-medium ">
        {{ item.title }}
      </NuxtLink>
      <p class="truncate ...">
        {{ item.body }}
      </p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(['data'])

console.log(props.foo)
</script>