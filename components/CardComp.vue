<template>
  <div>
    <div class="card bg-gray-100 w-[170px] h-[170px] m-auto flex shadow-lg hover:bg-gray-200 ">
      <div class="content flex m-auto justify-center items-center w-full">
        <div class="w-full h-full justify-center m-auto">
          <!-- <img :src="`/img/${item.icon}.svg`" class="w-[150px] p-4" alt="img" /> -->
          <div class="border-b-2 border-b-gray-300 pb-1">
            {{ item.title }}
          </div>
          <div>
            {{ item.stack }}
          </div>
        </div>
      </div>
    </div>
    <!-- <div class="mt-2">
      {{ item.title }}
    </div> -->
  </div>
</template>

<script setup lang="ts">
const props = defineProps({ item: { type: Object, required: true } })
const url = 'https://asset.cloudinary.com/dewaqintoro/d8f7d924b65e2183620a8aaada58cdf8'

</script>

<style lang="postcss" scoped>
.darkTheme:hover{
  background: rgb(61, 81, 94) !important;
}
.lightTheme:hover{
  background: #f1f1f1 !important;
}

.card {
  border-radius: 3rem 0 3rem 0;
}

</style>