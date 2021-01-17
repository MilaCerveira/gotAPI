<template>
    <div v-if="characterDetails" class="details-section">
        {{characterDetails.name}}
        {{characterDetails.gender}}
        {{characterDetails.culture}}
        {{characterDetails.books}}
        {{characterDetails.aliases}}
    </div>
</template>
<script>
export default {
    data(){
        return {
            characterDetails: null
        }
    },
    //step 1 tell vue what you are accepting from app.vue
    props: ['selectedCharacter'],
    // watches for a change on the property of the function name 
    watch: {
        selectedCharacter(updatedCharacter) {
            console.log('selectedCharacter is changed : ', updatedCharacter);
              fetch(updatedCharacter.url)
                .then(res => res.json())
                .then(characterDetails => this.characterDetails = characterDetails)
        }
    }
}
</script>
<style scoped>
.details-section {
  padding: 30px;
  border: 1px solid grey;
  border-radius: 10px;
  margin: 5%;
}
</style>