<template>
  <div class="card card-w70">
    <slot name="title"></slot>
    <slot name="avatar"></slot>
    <slot name="content"></slot>
    <slot name="default" v-if="!$slots.title && !$slots.avatar && !$slots.content">
      <h3>Добавьте первый блок, чтобы увидеть результат</h3>
    </slot>
  </div>
</template>

<script>
export default {};
</script>

<style>

</style>
