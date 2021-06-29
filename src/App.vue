<template>
  <Users :users="users" @childToParent="helloFromChild"/>
</template>

<script>
import Users from './components/Users.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Users
  },
  data: function () {
    return {
      users: null
    }
  },
  created: function () {
    axios
      .get('https://jsonplaceholder.typicode.com/users')
      .then(res => {
        this.users = res.data;
      })
  },
  methods: {
    helloFromChild (value) {
      console.log(value)
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
