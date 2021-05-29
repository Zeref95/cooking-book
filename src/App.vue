<template>
  <Header @click="goToPage('Main')"></Header>
  <button @click="goToPage('Recipe')">Recipe</button>
  <button @click="goToPage('CreateRecipe')">CreateRecipe</button>
  <component :is="currentTabComponent"></component>
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
    }
  },
  components: {
    Header,
    Main,
    Recipe,
    CreateRecipe
  },
  methods: {
    goToPage(pageName) {
      this.currentTabComponent = pageName;
    }
  }
}
</script>

<style>
.logo {
  width: 20%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
