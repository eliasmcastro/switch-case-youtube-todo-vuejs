<template>
  <div class="container-board">
    <div class="columns">
      <div class="column col-6 col-sm-12">
        <div class="panel">
          <div class="panel-header">
            <div class="panel-title">Todo</div>
          </div>
          <div class="panel-body">
            <todo
              v-for="todo in uncheckeds"
              :todo="todo"
              @remove="removeTodo"
              @toggle="toggleTodo"
              :key="todo.id"
            />
          </div>
          <div class="panel-footer">
            <button
              @click="checkAll"
              v-if="uncheckeds.length > 0"
              class="btn btn-link float-right"
            >Concluir tudo</button>
          </div>
        </div>
      </div>
      <div class="column col-6 col-sm-12">
        <div class="panel">
          <div class="panel-header">
            <div class="panel-title">Done</div>
          </div>
          <div class="panel-body">
            <todo
              v-for="todo in checkeds"
              :todo="todo"
              @remove="removeTodo"
              @toggle="toggleTodo"
              :key="todo.id"
            />
          </div>
          <div class="panel-footer">
            <button
              @click="uncheckAll"
              v-if="checkeds.length > 0"
              class="btn btn-link float-right"
            >Desmarcar tudo</button>
            <button
              @click="removeAllCheckeds"
              v-if="checkeds.length > 0"
              class="btn btn-link float-right text-error"
            >Remover tudo</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "@/components/Todo";
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Kamban",

  components: { 
    Todo 
  },

  methods: {
    ...mapActions([
      "removeTodo",
      "toggleTodo",
      "checkAll",
      "uncheckAll",
      "removeAllCheckeds"
    ])
  },

  computed: {
    ...mapGetters(["uncheckeds", "checkeds"])
  },
};
</script>

<style scoped>
.container-board {
  margin: 2rem 2rem 0;
  height: calc(100vh - 100px);
  padding-bottom: 20px;
}

.columns {
  height: 100%;
  justify-content: center;
}

.columns .column .panel {
  height: 80vh;
  border: 0;
  box-shadow: 0 0.25rem 1rem rgba(48, 55, 66, 0.15);
}

@media screen and (max-width: 600px) {
  .column:first-child {
    margin-bottom: 1rem;
  }
}
</style>