<template>
<div id='whisky'> 
<button class=delete v-on:click="delete_Whisky">Delete</button>
<h3 v-if="!modifdist" v-on:click="modifdist=true">Distillerie : {{whisky.dist}} </h3>
<div v-else class=form>
    <p> Modification distillerie : <input type="text" v-model="whisky.dist"> 
    <button class=save v-on:click="update_Whisky(whisky)">v</button>
    <button class=save v-on:click="modifdist=false">x</button></p>
</div>

<h3 v-if="!modifbout" v-on:click="modifbout=true">Bouteille : {{whisky.bout}} </h3>
<div v-else>
    <p>Modification bouteille : <input type="text" v-model="whisky.bout"> 
    <button class=save v-on:click="update_Whisky(whisky)">v</button>
    <button class=save v-on:click="modifbout=false">x</button> </p>
</div>

<h3 v-if="!modifprix" v-on:click="modifprix=true">Prix: {{whisky.prix}}€</h3>
<div v-else>
   <p>Modification prix :  <input type="number" v-model="whisky.prix"> 
    <button class=save v-on:click="update_Whisky(whisky)">v</button>
    <button class=save v-on:click="modifprix=false">x</button> </p>
</div>

<h3 v-if="!modifavis" v-on:click="modifavis=true">Avis : {{whisky.avis}} </h3>
<div v-else>
    <p> Modification avis : <br> <br> <input type="textarea" v-model="whisky.avis"  id=avis> 
    <button class=save v-on:click="update_Whisky(whisky)">v</button>
    <button class=save v-on:click="modifavis=false">x</button></p>
    
</div>

</div>


</template>
<script>
    export default {
        name:'Whisky', 
        props:['whisky'],
        data(){
            return{
                modifdist : false,
                modifbout : false,
                modifprix : false,
                modifavis : false,
            }
            
        },
        methods : {
            update_Whisky() {
                this.$emit('event_update', this.$props.whisky)
                this.modifdist=false
                this.modifbout=false
                this.modifprix=false
                this.modifavis=false
            },

            delete_Whisky() {
                console.log(whisky)
                this.$emit('event_delete', this.$props.whisky);
            }
        }
    }
</script>

<style>
.delete{
padding: 0.5rem;
padding-left: 0.8rem;
padding-right: 0.8rem;
border: none;
background: #8FBCE4;
border-radius: 3rem;

}



.delete:hover{
color : white; 
padding: 0.5rem;
padding-left: 0.8rem;
padding-right: 0.8rem;
border: none;
background: #1F293A;
border-radius: 3rem;
}

.save{
padding: 0.5rem;
padding-left: 0.8rem;
padding-right: 0.8rem;
border: none;
background: #8FBCE4;
border-radius: 3rem;
 
}



.save:hover{
color : white; 
padding: 0.5rem;
padding-left: 0.8rem;
padding-right: 0.8rem;
border: none;
background: #1F293A;
border-radius: 3rem;
}

#whisky{
      background-color: #236796;
        width: 55rem;
        margin: 20px auto;
        padding : 5px;
        border-radius : 3rem;
        ;
}

h3:hover{
color : white; 

border: none;
background: #1F293A;
border-radius: 3rem;
}

p{
color : white; 
padding: 0.5rem;
padding-left: 0.8rem;
padding-right: 0.8rem;
border: none;
background: #1F293A;
border-radius: 3rem;
}

input{
    background-color : #8FBCE4;
    border-color : #8FBCE4;
    border-radius: 2rem;
    color : white;
    font-weight: bold; 
    text-align : center; 

}
#avis{
    width : 35rem;
    height: 5rem;
}

</style>

//entourer avec une div, la mettre en flex, 
//align self sur la croix ou alors align item