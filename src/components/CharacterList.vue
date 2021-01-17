<template>
<div>
    <h2> List of Characters </h2>
<div v-for='(character, index) in characters' :key='character.url'> 
<p v-if="character.name"> {{index + 1}} {{character.name}} </p>
<p v-else> {{index + 1}} {{character.aliases[0]}} </p>
</div>
</div>
</template>


<script>
export default {
    data(){
        return{
            characters: []
        }
    },
    mounted(){
        fetch('https://www.anapioficeandfire.com/api/characters?page=1&pageSize=50')
        .then(res => res.json())
        .then(characters => {
            console.log(characters);
            this.characters = characters
        });
        

    }
}
</script>