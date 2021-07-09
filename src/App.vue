<template>
  <div>
    <div class="container grid-xs py-2">
      <img src="@/assets/logo.png" class="img-responsive img-logo mb-2" alt="Logo">
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input type="text" class="form-input" placeholder="Novo todo" v-model="todo.description">
          <button type="submit" class="btn btn-primary input-group-btn" :disabled="todo.description == ''">Adicionar</button>
        </div>
      </form>
      <div class="todo-list">
        <todo v-for="todo in todos" :key="todo.id" @toggle="toggleTodo" @remove="removeTodo" :todo="todo"/>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./components/Todo";

export default {
  name: "App",
  
  components: { 
    Todo
  },
  
  data() {
    return { 
      todos: [], 
      todo: { 
        id: 0,
        description: '',
        checked: false 
      } 
    };
  },

  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      
      this.todos.push(todo);
      
      this.todo = {
        id: 0,
        description: ''
      };
    },

    toggleTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id);
      if (index > -1) {
        const checked = !this.todos[index].checked;
        this.$set(this.todos, index, { ...this.todos[index], checked });
      }
    },

    removeTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id);
      if (index > -1) {
        this.$delete(this.todos, index);
      }
    }
  }
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.img-logo {
  max-width: 150px;
  margin: 0 auto;
}

.todo-list {
  padding-top: 2rem;
}
</style>
