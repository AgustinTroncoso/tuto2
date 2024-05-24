<script>
import Padre from "./components/Padre.vue";
import Hijo from "./components/Hijo.vue";

export default {
  components: {
    Padre,
    Hijo,
  },
  data() {
    return {
      mensajePadre: "Hola desde el padre", // Mensaje inicial del padre
      tareas: [],
      mensaje: "",
    };
  },
  methods: {
    fetchTareas() {
      fetch("http://localhost:3000/tareas")
        .then((response) => response.json())
        .then((data) => {
          this.tareas = data;
        });
    },
    actualizarTarea(index) {
      fetch("http://localhost:3000/tareas", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          index: index,
          completada: this.tareas[index].completada,
        }),
      })
        .then((response) => response.json())
        .then((data) => {
          console.log(`Tarea ${index} actualizada:
${data.completada}`);
        });
    },
  },
};
</script>
<template>
  <div id="app">
    <Padre />
    <Hijo />
  </div>
  <h2 v-if="mensaje">{{ mensaje }}</h2>
</template>
