<template>
  <div id="user-info">
      <p><b>{{ fullName }}</b>
      Email: <em>{{ user.email }}</em><br>
      Общий рейтинг: {{ ratings }}</p>
      <button @click="addRating">Поставить лайк</button>
  </div>
</template>

<script>
export default {
  name: 'UserInfo',
  data() {
    return {
      user: {
        id: 1,
        login: 'bumhunter',
        name: 'Alexandr',
        surname: 'Urusikov',
        email: 'archiref@yahoo.com',
        isAdmin: true
      },
      ratings: 0
    }
  },
  computed: {
    fullName() {
      return `${this.user.name} ${this.user.surname}`
    }
  },
  methods: {
    addRating() {
      this.ratings++;
    }
  },
  mounted() {
    this.addRating();
  },
  watch: {
    ratings(newValue) {
      if(newValue > 15) {
        console.log("Значение более 15");
      }
    }
  }
}
</script>

<style>
#user-info {
  float: right;
  width: 10%;
  margin-top: 60px;
  margin-right: 50px;
  padding: 35px;
  background: #fafafa;
  border: 1px solid #ebebeb;
  border-radius: 5px;
  box-shadow: 0px 1px 14px 0px rgba(0,0,0,0.15);
}

#user-info b {margin-bottom: 4px; display: block}

#user-info button {
  border: 0;
  background: #E06249;
  border-radius: 5px;
  color: #fff;
  font-weight: bold;
  padding: 10px;
  cursor: pointer;
  outline: none;
  transition: transform 600ms ease;
}

#user-info button:hover {
  transform: translateY(-5px);
}
</style>
