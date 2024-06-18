<template>
<form v-on:submit.prevent="submitForm">
  <div>
    <label for="username">id : </label>
    <input id="username" v-model="username" type="text" placeholder="아이디">
  </div>
  <div>
    <label for="password">pw : </label>
    <input id="password" v-model="password" type="password" placeholder="패스워드">
  </div>
  <button type = "submit">login</button>
</form>
</template>
<script>
import axios from 'axios';

export default {
  name: 'App',
  data: function () {
    return {
      username : '',
      password : ''
    }
  },
  methods : {
    submitForm : function () {
      //e.preventDefault();
      let url = 'https://jsonplaceholder.typicode.com/users';
      let data = {
        username : this.username,
        password : this.password
      }
      axios.post(url,data).then(function (response) {
        console.log(response);
      }).catch(function (error) {
        console.log(error);
      });

    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
