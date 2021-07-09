<template>
  <div class="container grid-xs py-2">
    <form @submit.prevent="add(todo)">
      <div class="input-group">
        <input type="text" class="form-input" placeholder="Novo todo" v-model="todo.description">
        <button type="submit" class="btn btn-primary input-group-btn" :class="{loading}" :disabled="todo.description == ''">Adicionar</button>
      </div>
    </form>
    <div class="todo-list">
      <todo v-for="todo in todos" :key="todo.id" @toggle="toggleTodo" @remove="removeTodo" :todo="todo"/>
    </div>
  </div>
</template>

<script>
import Todo from "@/components/Todo";

import { mapActions, mapState } from "vuex";

export default {
  name: "Home",
 
  components: { 
    Todo 
  },
  
  data() {
    return { 
      todo: { 
        id: 0,
        description: '',
        checked: false 
      }
    };
  },

  methods: {
    ...mapActions(["addTodo", "toggleTodo", "removeTodo"]),
    
    async add(todo) {
      await this.addTodo(todo);
      
      this.todo = {
        id: 0,
        description: '',
        checked: false
      };
    }
  },

  computed: {
    ...mapState(["todos", "loading"])
  },
};
</script>

<style scoped>
.container {
  margin-top: 2rem;
}

.todo-list {
  padding-top: 2rem;
}
</style>