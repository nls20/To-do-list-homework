<template>
  <div id="app">
    <ul>
      <li v-for="(todo, index) in todos" :key="index"
      v-bind:class="todo.priorityHigh ? 'priorityHigh' : 'priorityLow' ">
        <span>{{todo.name}}</span>
        <span>{{todo.priority}}</span>
        <button v-if="todo.priorityHigh" @click="clickTodo(index)">Make Low</button>
        <button v-if="todo.priorityLow" @click="clickTodo(index)">Make High</button>
      </li>
    </ul>

    <form v-on:submit.prevent="saveNewTodo">
      <label for="new-todo">Add a new To-do Task: </label>
      <input type="text" id="new-todo" v-model="newTodo">
      <input type="submit" value="Save New To-do Task">
    </form>
    <form v-on:submit.prevent="savePriority">
      <input type="radio" id="high" value="true" v-model="picked">
      <label for="high">High</label>
      <input type="radio" id="low" value="false" v-model="picked">
      <label for="low">Low</label>
    </form>
  </div>
</template>

<script>
export default {
 data() {
   return {
     todos: [
       {name: "Clean Car", priorityHigh: true},
       {name: "Do Shopping", priorityHigh: true},
       {name: "Do Dishes", priorityLow: false},
     ],
     newTodo: ""
   }
 },
 methods: {
   saveNewTodo: function() {
     this.todos.push({
       name: this.newTodo,
       priorityHigh: false
     });
     this.newTodo = "";
   
 },
  savePriority: function() {
    this.this.todos.push(
      this.priority
    );
    this.priority = "";
  },

 clickTodo: function(index) {
   this.todos[index].priorityHigh = false;
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

li.priorityHigh {
  border: 2px solid red;
}

li.priorityLow {
  border: 2px solid green;
}
</style>
