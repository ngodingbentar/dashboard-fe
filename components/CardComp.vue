<template>
  <div class="card bg-gray-100">
    <div class="content">
      <div>
        <!-- <p>hahs</p> -->
        <p>{{ item.title }}</p>
      </div>
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
  @apply px-4 pb-4 rounded-lg my-8;
  /* box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 10px 0 rgba(0, 0, 0, 0.15); */
  .btn-show {
    @apply text-center w-full;
  }
  .idSurah {
    @apply items-center justify-center flex rounded-full;
    width: 45px;
    height: 45px;
  }
  .content {
    @apply px-4 w-full;
  }
}

.arabic {
  @apply text-right text-3xl;
  line-height: 4rem !important;
}
.my-audio{
  max-width: 100%;
  height: 35px;
}
</style>