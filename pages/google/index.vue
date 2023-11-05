<template>
  <div class="p-8">
    <GoogleHeader @search="getAll" />
    <div v-if="loading" class="text-center mt-8">Loading...</div>
    <GoogleContent v-else :result="data" />
  </div>
</template>

<script setup>
const route = useRoute()
const tabActive = computed(() => route.query.tab || 'all')
const data = ref([])
const loading = ref(false)

async function getAll (payload, t) {
  if(payload === '') return
  loading.value = true
  let type = t
  if(t === 'all') {
    type = 'search'
  }
  try {
    const res = await fetch(`api/google-${type}?q=${payload}`)
    const convert = await res.json()
    data.value = convert.result
    loading.value = false
  } catch (error) {
    console.log(error)
    loading.value = false
  }
  // const res = await fetch(`api/google-${type}?q=${payload}`)
  // console.log('res', res)
}
</script>