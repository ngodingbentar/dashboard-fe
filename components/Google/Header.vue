<template>
  <div>
    <div class="flex justify-between">
      <input v-model="searchValue" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Search...">
      <div class="shadow appearance-none border rounded bg-gray-100 items-center flex px-4 ml-4">
        <button class="" @click="doSearch(tabActive)">Search</button>
      </div>
    </div>
    <GoogleTab @search="doSearch" />
  </div>
</template>

<script setup>
const emit = defineEmits(['search'])
const route = useRoute()

const activeTab = ref('all')
const tabActive = computed(() => route.query.tab || 'all')

const searchValue = ref('')
function doSearch (type) {
  emit('search', searchValue.value, type)
}
</script>