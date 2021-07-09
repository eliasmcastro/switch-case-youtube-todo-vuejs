<template>
  <div class="card">
    <div class="card-body">
      <div class="tile" :class="{checked: todo.checked}">
        <div class="tile-icon">
          <i class="icon" :class="todo.checked ? 'icon-check' : 'icon-time'"></i>
        </div>
        <div class="tile-content">
          <p class="tile-subtitle">{{ todo.description }}</p>
        </div>
        <div class="tile-action">
          <button @click="$emit('remove', todo)" class="btn btn-link">
            <span class="text-error">Remover</span>
          </button>
          <button @click="$emit('toggle', todo)" class="btn btn-link">
            <span v-if="todo.checked">Desmarcar</span>
            <span v-else>Concluído</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: { 
      type: Object, 
      required: true
    }
  }
};
</script>

<style scoped>
.card {
  margin-bottom: 15px;
}

.tile {
  align-items: center;
}

.checked {
  text-decoration: line-through;
  color: lightgray;
}

.tile-content {
  align-items: center;
}

p {
  margin: 0;
}
</style>
