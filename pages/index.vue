<template>
  <div class="flex m-auto justify-center">
    <div class="main text-center">
      <div v-for="item in thisIndex" :key="item.id">
        <nuxt-link v-if="item.type === 'int'" :to="item.route">
          <CardComp :item="item" />
        </nuxt-link>
        <a v-else :href="item.route" target="_blank">
          <CardComp :item="item" />
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
  import dataJson from '~/data/myindex.json'
  import dataExt from '~/data/extIndex.json'
import CardComp from '../components/CardComp.vue';

  const dataDoa = dataJson.data
  const extIndex = dataExt.data
  const thisIndex = computed(() => {
    const data = [...dataDoa, ...extIndex]
    const duh = data.sort(function (a, b) {
      if (a.title < b.title) {
        return -1
      }
      if (a.title > b.title) {
        return 1
      }
      return 0
    })
    return duh
  })
</script>


<style lang="postcss" scoped>
.darkTheme{
  /* color: rgb(61, 81, 94); */
  .card:hover{
    background: rgb(61, 81, 94);
  }
}
.lightTheme{
  .card:hover {
    background: #f1f1f1;
  }
}
.main {
  @apply pt-8 min-h-screen max-w-md;
}

.content {
  @apply my-8;
}
.item {
  @apply px-8 mx-36 my-4;
}
.card {
  @apply text-2xl p-4 rounded-lg;
}
</style>
