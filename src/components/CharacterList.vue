<template>
<div>
    <h2> List of Characters </h2>
<div v-for='(character) in characters' :key='character.url' @click='showDetails(character)'> 
<p v-if="character.name">  {{character.name}} </p>
<p v-else>  {{character.aliases[0]}} </p>
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
    props: ['handleCharacterSelection'],
    mounted(){
        fetch('https://www.anapioficeandfire.com/api/characters?page=1&pageSize=50')
        .then(res => res.json())
        .then(characters => {
            console.log(characters);
            this.characters = characters
        });
        

    },
    methods: {
        // alternative to eventBus passing the method as a property
    showDetails(character) {
        this.handleCharacterSelection(character);
        console.log(character);
    }
    }
}
</script>