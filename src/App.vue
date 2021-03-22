<template>
  <div id="app">
    <app-header></app-header>
    <recipes v-bind:dataRecipes="dataRecipes" v-bind:recipeToDisplay="recipeToDisplay"></recipes>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Recipes from './components/Recipes.vue';
export default {
  name: 'app',
  components:{
    'app-header': Header,
    'recipes': Recipes
  },
  data () {
    return {
     dataRecipes: [],
     url: '',
     recipeToDisplay: 1
    }
  },
   mounted(){
    //  this.url = 'http://localhost:8080/src/db/db.json';
    //  fetch(this.url)
    //   .then(response => response.json())
    //   .then(data => console.log(data));
      this.$http.get('http://localhost:8080/src/db/db.json').then(function(data){
        this.dataRecipes = data.body;
        let parsed = JSON.stringify(this.dataRecipes);
        localStorage.setItem('recipes', parsed);
      });
      
    }
}
</script>

<style>

</style>
