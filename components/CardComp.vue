<template>
  <div class="card bg-gray-100 w-[170px] h-[170px] m-auto flex p-2 shadow-lg">
    <div class="content flex m-auto justify-center items-center">
      {{ item.title }}
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({ item: { type: Object, required: true } })

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