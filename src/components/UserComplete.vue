<template>
    <div class="data-user" v-if="showUser">
        <div class="image-user">
            <img :src="data.avatar_url" alt="user-image">
        </div>

        <div>
            <ul>
                <li> <span class="bold">Nome:</span> <span>{{ data.name || '-' }}</span></li>
                <li> <span class="bold">Localização:</span> <span>{{ data.location || '-' }}</span> </li>
                <li>
                    <span class="bold"> Biografia:</span>
                    <p>
                        {{ data.bio || '-' }}
                    </p>    
                </li>
                <li> <span class="bold">Seguidores:</span> <span>{{ data.followers || '-' }}</span></li>
                <li> <span class="bold">Seguindo:</span> <span>{{ data.following || '-' }}</span></li>
            </ul>
        </div>
    </div> 
   
  </template>
  
  <script>
  export default {
    name: 'UserComplete',

    props:{
        data: Object,
        showUser:{
            type:Boolean,
            default: false        
        },
    },

    mounted() {
        console.log('data', this.data)
    }
  }
  </script>