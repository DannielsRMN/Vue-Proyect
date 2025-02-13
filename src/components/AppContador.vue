<template>
<div class="container">

  <h1>Contador</h1>

<!-- Variable que permite mostrar un dato reactivo en la vista -->

<div class="contador" :class  = "colorContador"> <!-- :class  = "colorContador"> | Sirve para asignar un CSS a esta clase-->
  {{contador}}
</div>

<!-- Botones que permiten realizar acciones en la vista -->

<div class="botones">
  <button @click="disminuir">Disminuir 5</button>
  <button @click="decrementar">Decrementar</button>
  <button @click="incrementar">Incrementar</button>
  <button @click="aumento">Aumentar 5</button>
</div>

</div>

</template>

<script setup>

//Importamos la función ref de vue, necesaria para usar datos reactivos
import { computed, ref } from 'vue';

//Creamos una variable reactiva, que inicia en cero (0)
const contador = ref(0);

//Funciones que permiten modificar el valor de la variable reactiva (Funcion de flecha)
const incrementar = () => {
  contador.value++;
}

const decrementar = () => {
  contador.value--;
}

const aumento = () => {
  contador.value = contador.value + 5;
}

const disminuir = () => {
  contador.value = contador.value - 5;
}

//Experimento de cambio de color

const colorContador = computed(() => { // Computed es una función que permite realizar cálculos reactivos
  if (contador.value > 0) {
    return 'green';
  } else if (contador.value < 0) {
    return 'red';
  } else {
    return 'grey';
  }
});

</script>

<style scoped>

/* Centra todo */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

/* Estilo del contador */
.contador {
  font-size: 50px;
  font-weight: bold;
  text-align: center;
  margin: 20px 0;
}

.green {
  color: green;
}

.red {
  color: red;
}

.grey {
  color: grey;
}

/* Estilo del h1 */

h1 {
  color: #4CAF50;
  font-size: 40px;
  font-weight: bold;
  text-align: center;
  margin: 20px 0;
}

/* Contenedor de los botones */
.botones {
  display: flex;
  justify-content: space-between;
  width: 50%; /* Puedes ajustar esto según el tamaño deseado */
}

/* Estilo de los botones */
button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 15px 32px;
  font-size: 16px;
  margin: 5px;
  cursor: pointer;
  border-radius: 5px;
  flex-grow: 1; /* Para que todos los botones tengan el mismo ancho */
}
</style>
