<template>
    <div v-if="characterDetails" class="details-section">
        {{characterDetails.name}}
        {{characterDetails.gender}}
        {{characterDetails.culture}}
        {{characterDetails.books}}
        {{characterDetails.aliases}}
         <iframe width="806" height="453" src="https://www.youtube.com/embed/70V1aWbmlwo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
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
  border: 5px solid #82A0BC;
  border-radius: 10px;
  margin: 5%;
  background-color: #82A0BC;
 

}
</style>