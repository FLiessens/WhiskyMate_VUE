<template>

<div id='whiskyList'><h2 >Mon bar</h2>
<div v-on:click="showAdd=true" v-if="!showAdd">
    <p class=bouton>[Ajouter un nouveau whisky]</p>
    </div>
<div v-else>
<Add @Added="ManageAdd"></Add>
</div>
    
    <div v-for ="whisky in whiskyList" :key="whisky.idwhisky">
<Whisky v-bind:whisky="whisky" @event_update="update" @event_delete="deleteWhisky"></Whisky>   
    </div>
</div>
</template>
 
<script>
//import d'axios
import axios from 'axios'
import Whisky from './whisky'
import Add from './Add'

    export default {
        name:'whiskyList',
        components: {Whisky, Add},
        data(){
            return{
                whisky:{
                    idwhisky:0, 
                    dist:"", 
                    bout:"", 
                    prix: 0,
                },
                showAdd: false,
                whiskyList:[],
                url:"http://localhost:3000/api/whisky/",


            }
        },
        methods : {
            get_whiskyList(){
                axios.get(this.url)
                .then( (response) => {
                    this.whiskyList=response.data.whiskies;
                    console.log(this.whiskyList)
                })
                .catch( (error) => {
                    console.log(error);
                })
            },
            
            ManageAdd(){
              this.showAdd=false 
              this.get_whiskyList()  
            },

            update(whisky) {
                axios.put(this.url + whisky.idwhisky, {dist:whisky.dist, bout:whisky.bout, avis:whisky.avis, prix:whisky.prix } )
                .then((response) => {console.log(response)})
                .catch((error) => {
                console.log(error);
                })
            },

            deleteWhisky(whisky) {
                axios.delete(this.url + whisky.idwhisky)
               .then((response) => {console.log(response)
                this.get_whiskyList();

               })
            
                .catch((error) => {
                console.log(error);
                })
            }, 
        }, 


        
            mounted(){
                 this.get_whiskyList();
        }
    }
</script>

<style>
#whiskyList{
    background-color : #1F293A;
    font-size : 25pt;
    padding : 5px;
    border-radius: 2rem;
    margin: 2rem;
}
#h2{
    font-size: 25pt;
}

.bouton{
border: none;
background: #236796;
border-radius: 3rem;
width: 55rem;
margin: 20px auto;
padding : 5px;
}

.bouton:hover{
color : black;
border: none;
background: #8FBCE4;
border-radius: 3rem;
width: 55rem;
margin: 20px auto;
padding : 5px;
}

input{
    height : 2rem;
    width: 10rem;
}
</style>
