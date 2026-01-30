<template>
  <div class="app">
    <header>
      <h1>Laravel 12 + Vue 3</h1>
      <p>Ejemplo de navegación entre tres vistas con Inertia.</p>
    </header>

    <nav class="nav">
      <button @click="goTo(route('home'))">Inicio</button>
      <button @click="goTo(route('vista1'))">Vista 1</button>
      <button @click="goTo(route('vista2'))">Vista 2</button>
    </nav>

    <main class="view">
      <slot />
    </main>
  </div>
</template>

<script setup>
import { router } from '@inertiajs/vue3';

const goTo = (url) => {
  router.get(url);
};
</script>

<style>
.app {
  max-width: 800px;
  margin: 2rem auto;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}

header h1 {
  color: #42b883;
  margin-bottom: 0.25rem;
}

.nav {
  margin: 1rem 0 2rem;
  display: flex;
  gap: 0.5rem;
}

.nav button {
  padding: 0.5rem 1rem;
  border-radius: 0.375rem;
  border: 1px solid #42b883;
  background: white;
  color: #42b883;
  cursor: pointer;
}

.nav button:hover {
  background: #42b883;
  color: white;
}
</style>