<template>
    <div class="c-loader"></div>
</template>

<script>
  export default {
    name: 'PageLoading',
  }
</script>

<style scoped>

.c-loader {
  border: 6px solid #e5e5e5;
  border-top-color: #51d4db;
  height: 50px;
  width: 50px;
  display: inline-block;
  margin-top: 1rem;
}

.c-loader {
  animation: is-rotating 1s infinite;
  border: 6px solid #e5e5e5;
  border-radius: 50%;
  border-top-color: #51d4db;
  height: 50px;
  width: 50px;
}

@keyframes is-rotating {
  to {
    transform: rotate(1turn);
  }
}
</style>