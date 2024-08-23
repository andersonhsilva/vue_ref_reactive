<script setup>
import { ref, reactive } from 'vue';

// ref para primitivos como: numero, strings e etc.
let count = ref(0);

// reactive para objetos
let courses = reactive([
  { title: "PHP" },
  { title: "Node" },
  { title: "JavaScript" },
  { title: "Vue" },
]);

let newCourse = {};

function increment() {
  count.value++;
}

function addCourse() {
  courses.push(newCourse);
  newCourse = {};
}
</script>

<template>
  <div>

    <h1>{{ count }}</h1>
    <button @click="increment">Incrementar</button>

    <h1>Lista de Cusos</h1>
    <ul>
      <li v-for="(course, index) in courses" :key="index">
        {{ course.title }}
      </li>
    </ul>

    <br>

    <input type="text" v-model="newCourse.title">
    <button @click="addCourse">Adicionar Curso</button>

  </div>
</template>

<style scoped></style>
