<template>
  <div class="container">
    <h3>Users:</h3>
    <button class="btn btn-primary" @click="enterFromChild">Enter</button>
    <table class="table">
      <thead>
        <th scope="col">Id</th>
        <th scope="col">Name</th>
        <th scope="col">Email</th>
        <th scope="col">City</th>
      </thead>
      <tbody v-if="users">
        <tr v-for="user in principalUsers" :key="user.id">
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
export default {
  name: 'Users',
  props: {
    users: Object
  },
  computed:{
    principalUsers () {
      return this.users.filter(user => user.id < 5)
    }
  },
  methods: {
    enterFromChild () {
      this.$emit('childToParent', 'hello from child')
    }
  }
}
</script>

<style>
h3 {
  margin-bottom: 5%;
}
</style>