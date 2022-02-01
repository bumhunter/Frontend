<template>
  <UserInfo />
  <PostItem />
</template>

<script>
import UserInfo from './components/UserInfo';
import PostItem from './components/PostItem';

export default {
  name: 'App',
  components: { UserInfo, PostItem }
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
