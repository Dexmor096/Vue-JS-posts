<template>
	<form class='form' @submit.prevent>
    <h1 style='margin-bottom: 5px;'>Создайте пост</h1>
    <my-input
      v-model='post.title'
      placeholder='введите Title'></my-input>
    <my-input
      v-model='post.body'
      placeholder='введите Body'></my-input>
    <my-button @click="createPost">Создать</my-button>
  </form>
</template>
<script>
import MyInput from './UI/MyInput.vue';

export default {
  components: { MyInput },
  data() {
    return {
      post: {
        title: '',
        body: '',
      }
    }
  },
  methods: {
    createPost() {
      this.post.id= Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: '',
      }
    }
  }
}
</script>
<style scoped>
.form {
  display: flex;
  flex-direction: column;
  margin-top: 10px;
}
</style>