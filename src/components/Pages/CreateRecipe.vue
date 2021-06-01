<template>
  <div class="container">
    Страница создания нового рецепта.
    <div class="form">
      <div class="form-group">
        <label for="title">Название</label>
        <input type="text" class="form-control" v-model="title" id="title" placeholder="Название">
      </div>
      <div class="form-group">
        <label for="description">Описание</label>
        <input type="text" class="form-control" v-model="description" id="description" placeholder="Описание">
      </div>
      <div class="form-group">
        <label for="content">Текст</label>
        <textarea class="form-control" v-model="content" id="content" rows="6"></textarea>
      </div>
      <button class="btn btn-success mt-1" @click="add">Создать</button>
    </div>

    <div class="alert alert-success" role="alert" v-if="status.success">
      Рецепт успешно создан, Вы можете добавить еще один рецепт, или вернуться на главную страницу.
    </div>
    <div class="alert alert-danger mt-1" v-if="status.failed" role="alert">
      Не все поля были успешно заполнены.
    </div>
  </div>
</template>

<script>
export default {
  name: "CreateRecipe",
  data() {
    return {
      title: '',
      description: '',
      content: '',
      status: {
        success: false,
        failed: false,
      }
    }
  },
  methods: {
    add() {
      this.status.success = false;
      this.status.failed = false;
      if (this.title && this.content && this.description) {
        this.$emit('addRecipe', {
          title: this.title,
          description: this.description,
          content: this.content,
        })
        this.title = '';
        this.description = '';
        this.content = '';
        this.status.success = true;
      } else {
        this.status.failed = true;
      }

    }
  }
}
</script>

<style scoped>

</style>