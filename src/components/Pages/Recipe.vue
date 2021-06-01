<template>
  <div>
    <h1>{{ recipe.title }}</h1>
    <p><b>{{ recipe.description }}</b></p>
    <p>{{ recipe.content }}</p>
  </div>
</template>

<script>
export default {
  name: "Recipe",
  props: ['recipes', 'currentRecipe'],
  data() {
    return {
      recipe: {
        title: '',
        description: '',
        content: '',
      }
    }
  },
  mounted() {
    this.recipe = this.recipes.find(recipe => recipe.id === this.currentRecipe)
  }
}
</script>

<style scoped>

</style>