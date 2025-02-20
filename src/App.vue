<script setup>
import Counter from './components/Counter.vue';
import { ref, reactive, computed, watch } from 'vue';

const contador = ref(0);
const obj = reactive({
  name: 'Alonso',
  apellido: 'Chavarria',
  edad: 25
})
const name = ref('Alonso');
const apellido = 'Chavarria';
const cantidad = ref(-1);
function aumentarContador() {
  contador.value++;
  obj.edad++;
  cantidad.value++;
}
const mensajeCantidad = computed(() =>{
    return cantidad.value > 0 ? 'Yes' : 'No';
});
const arreglo = ['hola', 'mundo', 'desde', 'vue', '3'];

watch(()=> obj.edad, (newVal, oldVal) => {
 if(newVal === 40){
  alert('Ya tienes 40 años');
 }
});

function mostrarMensajeDelHijo(){
  alert('Hola');
}
</script>

<template>
  <input type="text" v-model="name" @click="aumentarContador" />
  <h1 :id="name">Mi app en {{ name }} {{ apellido }}</h1>
  <hr>
  <button @click="aumentarContador">Aumentar</button>
  <h2>Contador: {{ contador }}</h2>
  <h2>Edad: {{ obj.edad }}</h2>
<hr>
<span :class="{ active: cantidad > 0 }">{{ mensajeCantidad }}</span>
<p v-if="cantidad > 0">si es mayor a  0</p>
<p v-else>no es mayor a  0</p>
<ul>
  <li v-for="i in arreglo" :key="i">
    {{ i }}
  </li>
</ul>
<hr>
<Counter titulo="Hola" valor-inicial="0" @hola="contador++"  />
<Counter titulo="adios" valor-inicial="10" @hola="mostrarMensajeDelHijo"  />
<Counter titulo="gol"  />
<Counter titulo="aqui"  />

</template>


