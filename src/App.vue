<template>
  <div id="app">
    <header @click="goToPage('Main')">
      <Header></Header>
    </header>

    <button class="btn btn-info" @click="goToPage('Main')">
      Книга рецептов
    </button>
    <button class="btn btn-secondary mx-1" @click="goToPage('CreateRecipe')">
      Создать новый рецепт
    </button>
    <hr>
    <component
        :recipes="recipes"
        @addRecipe="addRecipe"
        @goToCurrentRecipe="goToCurrentRecipe"
        :currentRecipe="currentRecipe"
        :is="currentTabComponent"
    ></component>
  </div>
</template>

<script>
import Header from './components/components/Header.vue'
import Main from './components/Pages/Main.vue'
import Recipe from "./components/Pages/Recipe";
import CreateRecipe from "./components/Pages/CreateRecipe";


export default {
  name: 'App',
  data() {
    return {
      currentTabComponent: 'Main',
      currentRecipe: 1,
      recipes: []
    }
  },
  components: {
    Header,
    Main,
    Recipe,
    CreateRecipe
  },
  mounted() {
    this.axios.get('https://api.coindesk.com/v1/bpi/currentprice.json').then((response) => {
      console.log(response.data)
    })
  },
  methods: {
    goToPage(pageName) {
      this.currentTabComponent = pageName;
    },
    addRecipe(newRecipe) {
      this.recipes.push(newRecipe)
    },
    goToCurrentRecipe(recipeId) {
      this.currentRecipe = recipeId.recipeId;
      this.currentTabComponent = 'Recipe'
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

header {
  cursor: pointer;
}
</style>
