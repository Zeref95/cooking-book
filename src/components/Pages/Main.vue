<template>
  <div>
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon1">Поиск по названию</span>
      </div>
      <input type="text" class="form-control" v-model="search" placeholder="Название рецепта">
      <p>обновление без перезагрузок</p>
    </div>

    <h3>последние 20 рецептов</h3>

    <div
        class="card text-center"
        v-for="recipe in showingRecipes"
        :key="recipe.id"
        @click="goToRecipe(recipe.id)"
    >
      <div class="card-body">
        <h3 class="card-title">{{ recipe.title }}</h3>
        <p class="card-text">{{ recipe.description }}</p>
      </div>
      <div class="card-footer text-muted">
        {{ recipe.content }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Main',
  props: ['recipes'],
  data() {
    return {
      showingRecipes: [],
      search: '',
    }
  },

  watch: {
    search: function () {
      this.goSearch();
    },
    recipes: function () {
      this.showingRecipes = this.recipes;
      this.goSearch();
    }
  },
  mounted() {
    this.goSearch();
  },
  methods: {
    goToRecipe(id) {
      this.$emit('goToCurrentRecipe', {
        recipeId: id,
      })
    },
    goSearch() {
      let recipes = this.recipes.slice(0);
      if (this.search !== '') {
        this.showingRecipes = recipes.filter(recipe => recipe.title.toLowerCase().includes(this.search.toLowerCase()));
      } else {
        this.showingRecipes = recipes;
      }
      this.showingRecipes.splice(20)
      this.showingRecipes.reverse();
    },
  }
}
</script>

<style scoped>

</style>
