<template>
  <div class="avatar">
    <img :src="src" alt="" />
  </div>
</template>

<script>
export default {
  props: {
    src: String
  }
};
</script>

<style>
  .avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: 150px;
  border-radius: 50%;
}
</style>
