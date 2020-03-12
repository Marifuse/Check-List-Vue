<template>
  <div id="app">
    <link href="https://fonts.googleapis.com/css?family=Gloria+Hallelujah&display=swap" rel="stylesheet">
    <!-- Titulo -->
    <h1 class="title">Lista de Tareas</h1>
    <!-- Formulario -->
    <form class="container">
      <label class="to-do">Tarea:</label>
      <input type="text" v-model="tarea"/> 
      <button class="form-b" @click.prevent="mostrarResult">Agregar Tarea</button>
    </form>
    <!-- Componente -->
    <ListaTarea :tareas="tareas" @BorrarTarea="borrarTarea"/>
  </div>
</template>

<script>
// Componente
import ListaTarea from './components/ListaTarea.vue'

// Funciones
export default {
  name: 'App',
  components: {
    ListaTarea
  },
  data() {
    return {
      tareas: [],
      tarea: ''
    }
  },
  methods: {
    // Función para mostrar tarea y no agregar nada si hay campo vacío
    mostrarResult: function() {
      if(this.tarea != "")
      this.tareas.push(this.tarea) 
      this.tarea = ''
    },
    // Funcion quitar tarea
    borrarTarea: function(index) {
      this.tareas.splice(index, 1)
    }
  }
}
</script>

<style>
    body {
      margin: 0;
      background-image: url(./assets/fondo.jpg);
      background-size: cover;
      background-repeat: no-repeat;
    }
   /* Contenedor */
    #app {
        font-size: 1.3em;
        font-family: 'Gloria Hallelujah', cursive;
        text-align: center;
        padding: 2em;
    }
    /* Titulo de la página */
    .title {
        font-size: 2.5em;
        color: crimson;
        text-decoration-line: underline;
        margin-top: 0;
    }
    /* Sección container */
    .to-do {
        font-size: 1.5em;
        color: crimson;
        margin-bottom: 0;
        margin-right: 1em;
    }
    input {
        width: 30%;
        background-color: white;
        color: crimson;
        text-align: center;
        font-size: 1em;   
        padding: 0.2em;   
        border-radius: 1em;
        border: 1px solid crimson;
        margin-right: 1em;

    }
    .form-b {
        width: 15%;
        background-color: crimson;
        color: white;
        font-family: 'Gloria Hallelujah', cursive;
        font-size: 0.8em;
        font-weight: bold;
        border-radius: 1em;
        border: 1px solid crimson;
        transition: .3s;
    }
    .form-b:hover {
      background-color: white;
      color: crimson;
    }
</style>
