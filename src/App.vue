<template>
  <div id="app">
    <h1>用户管理系统</h1>
    <button @click="loadUsers">加载用户</button>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.id }} - {{ user.name }} - {{ user.age }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      users: []
    }
  },
  methods: {
    loadUsers() {
      axios.get('http://localhost:8080/users')
        .then(response => {
          this.users = response.data.data
        })
        .catch(error => {
          console.error(error)
        })
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  padding: 20px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
}
</style>