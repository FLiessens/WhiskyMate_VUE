<template>
<div id="Add">
    <H3> Fiche de création </h3>

<p>Distillerie: <input type="text" v-model="whisky.dist"> </p>
<p>Nom de la bouteille: <input type="text" v-model="whisky.bout"></p>
<p>Prix: <input type="number" v-model="whisky.prix"></p>
    
<p>Qu'en avez-vous pensé ?
<input type="text" v-model="whisky.avis">
</p>
<button class="create" v-on:click="post_Whisky">Create</button>
<button class="create">Cancel</button>

</div>
</template>
<script>
import axios from 'axios'
    export default {
        name:'Add', 
        data(){
            return{
                whisky:{
                    idwhisky:"", 
                    dist:"", 
                    bout:"", 
                    prix:0 ,
                },
                url:"http://localhost:3000/api/whisky/",
            }
        },
        methods : {
            post_Whisky() {
                axios.post(this.url, {dist:this.whisky.dist, bout:this.whisky.bout, avis:this.whisky.avis, prix:this.whisky.prix })
                .then ((response) => {
                    console.log(response.data);
                    this.$emit("Added")
                })
                .catch((error) => {
                    console.log(error);
                })
            },
        }
    }
</script>

<style>

.create{
border: none;
background: #8FBCE4;
border-radius: 3rem;
padding-top: 0.5rem;
padding-right: 2rem;
padding-bottom: 0.5rem;;
padding-left: 2rem;
}



.create:hover{
color : white; 

border: none;
background: #1F293A;
border-radius: 3rem;
padding-top: 0.5rem;
padding-right: 2rem;
padding-bottom: 0.5rem;;
padding-left: 2rem;
}

#Add{
      background-color: #236796;
        width: 55rem;
        margin: 20px auto;
        padding : 5px;
        border-radius : 3rem;
        ;
}
</style>