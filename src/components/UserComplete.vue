<template>
    <div class="data-user" v-if="showUser">
        <div class="image-user">
            <img v-bind:src="userAvatarUrl" alt="user-image">
        </div>

        <div>
            <ul>
                <li> <span class="bold">Nome:</span> <span>{{ nameUser }}</span></li>
                <li> <span class="bold">Localização:</span> <span>{{ userLocation }}</span> </li>
                <li>
                    <span class="bold"> Biografia:</span>
                    <p>
                        {{ userBio }}
                    </p>    
                </li>
                <li> <span class="bold">Seguidores:</span> <span>{{ userFollowers }}</span></li>
                <li> <span class="bold">Seguindo:</span> <span>{{ userFollowing }}</span></li>
            </ul>
        </div>
    </div> 
   
  </template>
  
  <script>
  export default {
    name: 'UserComplete',

    props:{
        nameUser:{
            type:String,
            default:''
        },

        userLocation:{
            type:String,
            default:''
        },

        userBio:{
            type:String,
            default:''
        },

        userFollowers:{
            type:String,
            default:''
        },
        
        userFollowing:{
            type:String,
            default:''
        },

        userAvatarUrl:{
            type:String,
            default: ''        
        },

        showUser:{
            type:Boolean,
            default: false        
        },
     }
  }
  </script>