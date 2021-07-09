<template>
  <div>
    <div class="container grid-lg">
      <header class="navbar pt-2">
        <section class="navbar-section">
          <router-link to="/" class="btn btn-link">Home</router-link>
          <router-link to="/kanban" class="btn btn-link">Kanban</router-link>
        </section>
        <section class="navbar-center">
          <img src="@/assets/logo.png" class="img-responsive img-logo" alt="Logo" />
        </section>
        <section class="navbar-section">
          <a href="https://github.com/eliasmcastro/switch-case-youtube-todo-vuejs" class="btn btn-link" target="_blank">GitHub</a>
        </section>
      </header>
      <router-view />
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.img-logo {
  max-width: 50px;
}
</style>