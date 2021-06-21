<template>
  <div class="container">
    <h3>Users:</h3>
    <table class="table">
      <thead>
        <th scope="col">Id</th>
        <th scope="col">Name</th>
        <th scope="col">Email</th>
        <th scope="col">City</th>
      </thead>
      <tbody v-if="users">
        <tr v-for="user in usersInBosnia" v-bind:key="user.id">
          <td scope="row">{{ user.id }}</td>
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.address.city }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Users',
  data: function (){
    return {
      users: null,
    }
  },
  created: function () {
    axios
      .get('https://jsonplaceholder.typicode.com/users')
      .then(res => {
        this.users = res.data;
      })
  },
  computed:{
    usersInBosnia () {
      return this.users.filter(user => user.id < 5)
    }
  }

}
</script>

<style>
h3 {
  margin-bottom: 5%;
}
</style>