<template>
  <div id="app">
    <img src="./assets/logo.png" class="logo">
    <h1>{{ title }}</h1>
    
    <input type="text" v-model="task" v-on:keyup.enter="addTask" placeholder="Add new task">

    <ul>
      <li v-for="(item, $index) in list">
        <todo-item v-bind:item="item" v-on:remove="deleteTask($index)"></todo-item>
      </li>
    </ul>
  </div>
</template>

<script>
  import TodoItem from './todo-item.vue'

  export default {
    name: 'todoList',
    
    data () {
      return {
        title: 'To-do List',
        task: '',
        list: []
      }
    },

    components: {
      TodoItem
    },

    methods: {
      addTask() {
        if (this.task !== '') {
          this.list.push({ text: this.task })
          this.task = ''
        }
      },

      deleteTask(index) {
        this.list.splice(index, 1)
      }
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.logo {
  width: 100px;
}

input[type="text"] {
  width: 350px;
  text-align: center;
  font-size: 1em;
  color: #41B883;
  padding: .4em;
  margin-bottom: 1em;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 10px;
}

a {
  color: #42b983;
}
</style>
