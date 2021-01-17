<template>
<div>
</div>
</template>

<script>
export default {
    data(){
        return{
            charaters: []
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