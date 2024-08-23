<script setup>
import { ref, reactive } from 'vue';
import Progress from './components/Progress.vue';

// ref para primitivos como: numero, strings e etc.
let count = ref(0);

// reactive para objetos
let courses = reactive([
  {
    title: "PHP",
    done: true,
  },
  {
    title: "Node",
    done: false,
  },
  {
    title: "JavaScript",
    done: true,
  },
  {
    title: "Vue",
    done: false,
  },
]);

let newCourse = { done: false };

function increment() {
  count.value++;
}

function addCourse() {
  courses.push(newCourse);
  newCourse = { done: false };
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

    <br><br>

    <Progress :courses="courses" />

  </div>
</template>

<style scoped></style>
