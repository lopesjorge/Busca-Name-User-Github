<template>
    <div class="c-loader" v-if="showLoading"></div>
</template>

<script>
  export default {
    name: 'PageLoading',

    props:{
        showLoading:{
            type:Boolean,
            default:false
        }
     },
     methods:{
        close(){
            this.$emit('close');
            console.log('caiu no close filho');
        }
     }
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