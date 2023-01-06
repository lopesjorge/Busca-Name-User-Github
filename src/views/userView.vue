<template>
    <div class="card-container">
        <div class="card-wrapper">
            <div class="card">
                <div class="input-user">
                <h1>Digite seu user Github</h1>
                <input type="text" placeholder="nome de usuário" v-model="nameUser" @keypress.enter="getData">
                <button @click="getData">Pesquisar</button>
                </div>

                <div class="data-user">
                    <div class="image-user">
                        <img v-bind:src="dataUser.avatarUrl" alt="user-image">
                    </div>

                    <div>
                        <ul>
                            <li> <span class="bold">Nome:</span> <span>{{ dataUser.login }}</span></li>
                            <li> <span class="bold">Localização:</span> <span>{{ dataUser.localizacao }}</span> </li>
                            <li>
                               <span class="bold"> Biografia:</span>
                                <p>
                                   {{ dataUser.biografia }}
                                </p>    
                            </li>
                            <li> <span class="bold">Seguidores:</span> <span>{{ dataUser.seguidores }}</span></li>
                            <li> <span class="bold">Seguindo:</span> <span>{{ dataUser.seguindo }}</span></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default{
    
    data(){
        return{
            nameUser:'',
            dataUser:{
                login:'',
                localizacao:'',
                biografia:'',
                seguidores:'',
                seguido:'',
                avatarUrl:''
            }
        }
    },

    methods:{
        
        getData(){
         fetch('https://api.github.com/users/lopesjorge')
            .then((response)=>{
                return response.json()
            }).then((data)=>{
                
                console.log(data)
               
                this.dataUser.login = data.login;
                this.dataUser.localizacao = data.location;
                this.dataUser.biografia = data.bio;
                this.dataUser.seguidores = data.followers;
                this.dataUser.seguindo = data.following;
                this.dataUser.avatarUrl = data.avatar_url;
                
                console.log('---------------------------------');

                console.log('Dados de usuário GITHUB ');
                console.log('Name user GITHUB: ',this.dataUser.login);
                console.log('Location: ',this.dataUser.localizacao);
                console.log('Bio:',this.dataUser.biografia);
                console.log('Seguidores: ',this.dataUser.seguidores);
                console.log('Seguindo: ',this.dataUser.seguindo);
                console.log('---------------------------------');
               
            })             
            console.log('dataUser',this.dataUser.login);
        }
 },

 computed:{
      fullName(){
       return `${this.urlgit}${this.nameUser}`     
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

.bold{
    color: black;
    font-weight: bold;
}
</style>