<template>
    <div class="card-container" v-if="showError">
        <div class="card-wrapper">
            <div class="card">
                <img src="../assets/icons8-nada-foi-encontrado-96.png" alt="">

                <span>
                    {{message}}
                </span> 

               <button @click="close()">
                    <span>
                       x
                    </span>
               </button>
               
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: 'UserComplete',

    props:{
        message:{
            type:String,
            default:''
        },
        showError:{
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

.card{
    display: flex;
    justify-content: space-between;
}

.card-container{
    width: 100vw;
    height: 30vh;
}
.card-wrapper{
    margin-top: -40rem;
    width: 30rem;
    height: auto;
    border: 1.5px solid red;
    border-radius: 10px;
    background-color: #FF00001A;
}

img{
    width: 24px;
    height: 24px;
    margin-right: -15rem;
    margin-top: -5px;
}
button{
    background-color: #FF00001A;
    border-radius: 4px;
    border-color: red;
}
span{
    color: red;
    font-weight: bold;
    text-align: center;
}
</style>