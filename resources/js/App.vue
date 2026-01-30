<template>
  <div class="app">
    <header>
      <h1>Laravel 12 + Vue 3</h1>
      <p>Ejemplo de navegación entre tres vistas hechas con Vue.</p>
    </header>

    <nav class="nav">
      <button @click="goTo('/')">Inicio</button>
      <button @click="goTo('/vista1')">Vista 1</button>
      <button @click="goTo('/vista2')">Vista 2</button>
    </nav>

    <main class="view">
      <component :is="currentViewComponent" />
    </main>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue';
import HomeView from './views/HomeView.vue';
import VistaUno from './views/VistaUno.vue';
import VistaDos from './views/VistaDos.vue';

const path = ref(window.location.pathname);

const currentViewComponent = computed(() => {
  if (path.value === '/vista1') return VistaUno;
  if (path.value === '/vista2') return VistaDos;
  return HomeView;
});

const goTo = (target) => {
  if (target === path.value) return;
  window.location.href = target;
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

.view h2 {
  margin-bottom: 0.5rem;
}

.view p {
  margin: 0;
}
</style>
