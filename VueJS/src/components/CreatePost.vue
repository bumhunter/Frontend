<template>
  <form @submit.prevent="createNewArticle" :class="{'error': maxCharacters > 70}">
    <label for="title"><b>Название:</b></label>
    <input type="text" id="title" placeholder="Введите название" v-model="state.newArticleTitle">
    <label for="text"><b>Основной текст:</b> <span>{{ maxCharacters }}/70</span></label>
    <textarea id="text" placeholder="Введите основной текст" v-model="state.newArticleText"></textarea>
    <button>Добавить</button>
  </form>
</template>

<script>
import { reactive, computed } from 'vue';

export default {
  name: 'CreatePost',

  setup(props, ctx) {
    const state = reactive({
      newArticleTitle: '',
      newArticleText: ''
    });

    const maxCharacters = computed(() => state.newArticleText.length);

    function createNewArticle() {
      if(state.newArticleTitle && state.newArticleText) {
        ctx.emit('add-post', state.newArticleText, state.newArticleTitle);
        state.newArticleText = ''
        state.newArticleTitle = ''
      }
    }

    return {
      state,
      maxCharacters,
      createNewArticle
    }
  }
}
</script>

<style>
form {
  float: right;
  width: 15%;
  padding: 35px;
}

form > * {display: block}
form > label {margin: 7px 0}
form > input, form > textarea {
  border: 1px solid silver;
  border-radius: 5px;
  font-size: 14px;
  padding: 10px;
  resize: none;
}

form > textarea {height: 100px}

form > button {
  border: 0;
  background: #E06249;
  border-radius: 5px;
  color: #fff;
  font-weight: bold;
  padding: 10px;
  cursor: pointer;
  outline: none;
  margin-top: 15px;
  transition: transform 600ms ease;
}

form > button:hover {
  transform: translateY(-5px);
}

form > label > span {
  color: #E06249;
  font-weight: bold;
  display: block;
  margin: 5px 0;
}

form.error > label[for='text'] {color: #E06249}
form.error > textarea {border-color: #E06249}
</style>
