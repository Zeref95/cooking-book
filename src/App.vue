<template>
  <div id="app">
    <header @click="goToPage('Main')">
      <Header></Header>
    </header>

    <button class="btn btn-info" @click="goToPage('Recipe')">
      Конкретный рецепт
    </button>
    <button class="btn btn-secondary mx-1" @click="goToPage('CreateRecipe')">
      Создать новый рецепт
    </button>
    <hr>
    <component :is="currentTabComponent"></component>
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
