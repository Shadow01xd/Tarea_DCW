<script setup>
import {ref} from "vue";

const tareas = ref([
  { titulo: 'Laboratorio', completada: false },
  { titulo: 'Parcial', completada: false },
  { titulo: 'Practicas', completada: false }
]);

const fechaNacimiento = ref('');
const edad = ref(null);

function calcularEdad() {
  if (fechaNacimiento.value) {
    const hoy = new Date();
    const fechaNac = new Date(fechaNacimiento.value);
    let anios = hoy.getFullYear() - fechaNac.getFullYear();

    const mes = hoy.getMonth() - fechaNac.getMonth();
    if (mes < 0 || (mes === 0 && hoy.getDate() < fechaNac.getDate())) {
      anios--;
    }
    edad.value = anios;
  }
}

/*
const url = ref("https://campus.univo.edu.sv/");

const frutas = ref(["Manzana", "Banana", "Cereza"]);

const contador = ref(1);

const  name = "soy estudiante"; 


defineProps({
    title: String,
    description: String,
});*

const count = ref(0);
const increment  = () =>{
    count.value++;
}
*/
</script>

<template>
  <!-- <h3>{{ name }}</h3>
   <h2>{{ title }}</h2>
   <p>{{ description }}</p>
   <p>{{ count }}</p>
<button @click="increment()">presiona aqui</button>*
<a :href="url">Link al campus</a>

<ul>
    <li v-for="fruta in frutas">{{ fruta }} </li>
</ul>

<h2 v-if="contador> 0">si es mayor que cero</h2>
<h2 v-else>no es mayor que cero</h2>/-->


<h1>Ejercicio 1</h1>
<div>
    <h1>Lista de Tareas</h1>
    <ul>
      <li v-for="(tarea, index) in tareas" :key="index">
        <input type="checkbox" v-model="tarea.completada" />
        <span>{{ tarea.titulo }}</span>
        <span v-if="tarea.completada"> - Tarea completada</span>
        <span v-else> - Tarea pendiente</span>
      </li>
    </ul>
  </div>

  <br>

  <h1>Ejercicio 2</h1>
  <div>
    <h1>Calculadora de Edad</h1>
    <form @submit.prevent="calcularEdad">
      <label for="fechaNacimiento">Fecha de Nacimiento:</label>
      <input type="date" id="fechaNacimiento" v-model="fechaNacimiento" />
      <button type="submit">Calcular Edad</button>
    </form>

    <div v-if="edad !== null">
      <p>Tu edad es: {{ edad }} años</p>
      <p v-if="edad >= 18">Eres mayor de edad</p>
      <p v-else>Eres menor de edad</p>
    </div>
  </div>

</template>