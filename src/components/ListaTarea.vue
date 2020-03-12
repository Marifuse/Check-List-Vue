<template>
  <div class="main">
    <!-- Lista de tareas que se muestran en el index -->
    <ul class="list-container" v-for="(tarea, index) in tareas" :key="index">
       <li class="list-t">{{tarea}}<button class="list-b" @click="EliminarTarea" v-bind:value="index">Eliminar</button></li>
     </ul>
  </div>
</template>

<script>
// Funciones
export default {
  name: 'ListaTarea',
  props: {
    tareas: Array
  },
  methods: {
    // Función del boton para quitar la tarea
    EliminarTarea: function(event) {
      let index = event.target.value
      this.$emit('BorrarTarea', index)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    /* Lista */
    .list-container {
        list-style: none;
        display: flex;
        width: 30%;
        margin: auto;
        margin-top: 1em;
    }
    .list-b {
        width: 10em;
        background-color: crimson;
        color: white;
        font-family: 'Gloria Hallelujah', cursive;
        font-size: 0.7em;
        font-weight: bold;
        margin-left: 1em;
        transition: .3s;
        border: none;
        border-radius: 1em;
    }
    .list-b:hover {
        background-color: black;
    }
</style>
