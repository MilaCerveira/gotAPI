<template lang="html">
<div>  
   <div class= "hero-bg"> 
        <section class = "top">
            <header> 
                <a href="#">Game of Thrones</a>
            </header>
            <h1> <span> “A man with no motive is a man     </span> <span> no one suspects.  </span> Always keep your foes <span>confused.” </span></h1>
        </section>
       </div>
       {{quote.quote}}
       {{quote.character}}
   </div>
</template>


<script>
import CharacterList from './components/CharacterList.vue'
export default {
  data(){
    return{
      quote: '',

    }
  },
  components: {

  },
  methods: {

  },
  mounted(){
  fetch('https://got-quotes.herokuapp.com/quotes')
  .then(res => res.json())
  .then(quote => this.quote = quote)
  }

}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@500&display=swap');
.hero-bg {
  background:#82A0BC
    url("https://traveladestatic.imgix.net/media/image/game-of-thrones-iceland_UCcbF3e.jpg?auto=format&crop=fit&fit=crop&h=504&w=1000&q=55&auto=format");
  background-size: 100% 400px;
  color: rgb(64, 64, 64);
  text-align: center;
  padding-bottom: 7em;
  background-repeat: no-repeat;
  background-attachment: fixed;
  
}
img {
  width: 100%;
}
.hero-bg a {
  color: rgb(64, 64, 64);
  text-decoration: none;
  font-weight: bold;
  font-size: 2rem;
  font-family: 'Cinzel', serif;
}

h1 {
  font-size: 2.5rem;
  margin: 2em 0 1.2em;
  color: rgb(64, 64, 64);
}

h1 span {
  text-transform: uppercase;
  display: block;
  font-size: 1.4rem;
  position: relative;
  z-index: 1;
  color: rgb(64, 64, 64);
}
h1 span::before {
  content: " ";
  position: absolute;
  width: 3em;
  background: #82A0BC;
  height: 0.4em;
  bottom: 0;
  z-index: -1;
  margin-left: -0.3em;
}
.hero-bg p {
  font-weight: bold;
  margin: 0 1em 3em;
}
header {
  padding: 1em 0;
}
</style>