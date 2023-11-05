<template>
  <div class="mt-4">
    <div class="flex">
      <div class="mx-1 cursor-pointer" @click="setTab('all')">
        <div class="px-4">All</div>
        <div v-if="activeTab === 'all'" class="h-1 bg-blue-500"></div>
      </div>
      <div class="mx-1 cursor-pointer" @click="setTab('images')">
        <div class="px-4">Images</div>
        <div v-if="activeTab === 'images'" class="h-1 bg-blue-500"></div>
      </div>
      <div>Images</div>
      <div>Videos</div>
      <div>News</div>
    </div>
  </div>
</template>

<script setup lang="ts">
const router = useRouter()
const activeTab = ref('all')

function setTab (tab) {
  activeTab.value = tab
  router.replace({
    query: {
      tab,
      ...router.query
    }
  })
}
</script>