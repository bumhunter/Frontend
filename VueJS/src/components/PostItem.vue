<template>
  <div id="articles">
    <div v-for="post in articles" :key="post.id" @click="deletePost(post.id)">
      <h2>{{ post.title }}</h2>
      <p>{{ post.text }}</p>
    </div>
  </div>

  <CreatePost v-on:add-post="createNewArticle" />
</template>

<script>
import CreatePost from './CreatePost';

export default {
  name: 'PostItem',
  components: { CreatePost },
  data() {
    return {
      articles: [
        {id: 1, text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.', title: 'Первая статья'},
        {id: 2, text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.', title: 'Вторая статья'},
        {id: 3, text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.', title: 'Третья статья'}
      ]
    }
  },
  methods: {
    deletePost(id) {
      let newArr = [];
      this.articles.forEach(item => {
        if(item.id != id)
          newArr.push(item);
      });
      this.articles = newArr;
    },
    createNewArticle(newArticleText, newArticleTitle) {
      this.articles.unshift({
        id: this.articles.length + 1,
        text: newArticleText,
        title: newArticleTitle
      });
    }
  }
}
</script>

<style>
#articles {
  float: left;
  max-width: 70%;
  margin: 70px;
}

#articles > div {
  background: #fafafa;
  border-radius: 5px;
  border: 1px solid silver;
  margin-bottom: 20px;
  padding: 30px;
}

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
