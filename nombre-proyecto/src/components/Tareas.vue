<template>
  <main class="tareas-app">
    <section class="tareas-panel">
      <h1>Mis tareas</h1>
      <form class="tareas-form" @submit.prevent="agregarTarea">
        <input
          v-model="nuevaTarea"
          placeholder="Escribe una nueva tarea"
          aria-label="Nueva tarea"
        />
        <button type="submit">Agregar</button>
      </form>

      <button class="toggle-button" type="button" @click="mostrar = !mostrar">
        {{ mostrar ? 'Ocultar tareas' : 'Mostrar tareas' }}
      </button>

      <ul v-if="mostrar && tareas.length" class="lista-tareas">
        <li v-for="(tarea, index) in tareas" :key="index">{{ tarea }}</li>
      </ul>

      <p v-else-if="!tareas.length" class="sin-tareas">No hay tareas registradas</p>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      nuevaTarea: '',
      tareas: [],
      mostrar: true
    }
  },
  methods: {
    agregarTarea() {
      if (this.nuevaTarea.trim()) {
        this.tareas.push(this.nuevaTarea);
        this.nuevaTarea = '';
      }
    }
  }
}
</script>
