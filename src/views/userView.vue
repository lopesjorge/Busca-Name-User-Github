<template>
    <div class="card-container">
        <div class="card-wrapper">
            <div class="card">
                <div class="input-user">
                <h1>Digite seu user Github</h1>
                <input type="text" placeholder="nome de usuário" v-model="nameUser" @keypress.enter="hiddenLoading(),getData()">
                <button @click="hiddenLoading(),getData()" class="btn-submit">Pesquisar</button>
                </div> 

                <PageLoading
                :showLoading="showLoading"
                >
                </PageLoading>

                <UserComplete 
                :nameUser="dataUser.login"
                :userLocation="dataUser.localizacao"
                :userBio="dataUser.biografia"
                :userFollowers="dataUser.seguindo"
                :userFollowing="dataUser.seguidores"
                :userAvatarUrl="dataUser.avatarUrl"
                :showUser="showUser"
                >
                </UserComplete>  
                
            </div>
        </div>
    </div>

    <UserNotFound
    @close="closeButton()"
    :showError="showError"
    :message="messageError" >
    </UserNotFound>

</template>

<script>
import UserComplete from '@/components/UserComplete.vue'
import UserNotFound from '@/components/UserNotFound.vue'
import PageLoading from '@/components/PageLoading.vue'

export default{
name: 'HomeView',

components: {
    UserComplete,
    UserNotFound,
    PageLoading
},
    data(){
        return{
            nameUser:'',
            apiUrl:'https://api.github.com/users/',
            messageError:'',
            showUser:false,
            showError:false,
            showLoading:false,
            dataUser:{
                login:'',
                localizacao:'',
                biografia:'',
                seguidores:'',
                seguido:'',
                avatarUrl:''
            },
        }
    },

    methods:{
        getData(){
         fetch(this.apiUrl+this.nameUser)
            .then((response)=>{
                return response.json()
            }).then((data)=>{
                
                if(data.message === 'Not Found'){
                    this.messageError = `User ${data.message}`;
                    this.showError = true;
                    this.showUser = false;
                    this.showLoading = false;

                    console.log('message:',data.message);
                    console.log('message:',data.message);
                    
                } else {
 
                this.dataUser = data;
                this.showUser = true;
                this.showError = false;

                this.dataUser.login = data.login || '-';
                this.dataUser.localizacao = data.location || '-';
                this.dataUser.biografia = data.bio || '-';
                this.dataUser.seguidores = data.followers || '-';
                this.dataUser.seguindo = data.following || '-';
                this.dataUser.avatarUrl = data.avatar_url || '/src/assets/logotipo-do-github.png';
                
                console.log('---------------------------------');

                console.log('Dados de usuário GITHUB ');
                console.log('Name user GITHUB: ',this.dataUser.login);
                console.log('Location: ',this.dataUser.localizacao);
                console.log('Bio:',this.dataUser.biografia);
                console.log('Seguidores: ',this.dataUser.seguidores);
                console.log('Seguindo: ',this.dataUser.seguindo);
                console.log('---------------------------------');

                this.showLoading = false;

                }
            })             
        },

        closeButton(){
        this.showError = false;
        console.log('caiu no close pai');
        },

        hiddenLoading(){
            this.showLoading = true;
        }
 }

   
}
</script>

<style>

.card-container{
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding-bottom: 1rem;
}

.card-wrapper{
    width: 30rem;
    height: auto;
    border: 1px solid black;
    border-radius: 10px;
}

.card{
    padding: 1rem;
}

.image-user{
    width: 10rem;
    height: 10rem;
    justify-items: center;
    margin: 2rem auto;
}

img{
    display: flexbox;
    width: 8rem;
    height: 8rem;
    border-radius: 50%;
}
ul{
    padding-left: 1rem;
    list-style: none;
    text-align: justify;
}
li{
    margin-bottom: 10px;
}

input{
    width: 15.5rem;
    height: 1.5rem;
}

.bold{
    color: black;
    font-weight: bold;
}

.btn-submit{
    margin-left: 10px;
    height: 1.9rem;
}

</style>