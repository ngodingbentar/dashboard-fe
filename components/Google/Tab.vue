<template>
  <div class="mt-4">
    <div class="flex">
      <div class="mx-1 cursor-pointer" @click="setTab('all')">
        <div class="px-4">All</div>
        <div v-if="tabActive === 'all'" class="h-1 bg-blue-500 mt-1"></div>
      </div>
      <div class="mx-1 cursor-pointer" @click="setTab('images')">
        <div class="px-4">Images</div>
        <div v-if="tabActive === 'images'" class="h-1 bg-blue-500 mt-1"></div>
      </div>
      <div class="mx-1 cursor-pointer" @click="setTab('videos')">
        <div class="px-4">Videos</div>
        <div v-if="tabActive === 'videos'" class="h-1 bg-blue-500 mt-1"></div>
      </div>
      <!-- <div>Images</div>
      <div>Videos</div>
      <div>News</div> -->
    </div>
  </div>
</template>

<script setup lang="ts">
const router = useRouter()
const route = useRoute()

const activeTab = ref('all')
const tabActive = computed(() => route.query.tab || 'all')

function setTab (tab) {
  // activeTab.value = tab
  router.replace({
    query: {
      tab,
      ...router.query
    }
  })
}
</script>