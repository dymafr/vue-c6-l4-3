<template>
  <form @submit.prevent="ajoutTodo">
    <label for="add-todo">Ajouter une todo </label>
    <input v-model="tache" id="add-todo" placeholder="Tâche à effectuer..." />
    <button>Ajouter</button>
  </form>
  <ul>
    <template v-for="(todo, index) in todos" :key="todo.id">
      <li>
        {{ todo.titre }}
        <button @click="suppTodo(todo.id)">Supprimer</button>
      </li>
    </template>
  </ul>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tache = ref('');
const todos = ref([
  {
    id: 1,
    titre: 'Apprendre HTML',
  },
  {
    id: 2,
    titre: 'Apprendre CSS et Sass',
  },
  {
    id: 3,
    titre: 'Apprendre JavaScript',
  },
  {
    id: 4,
    titre: 'Apprendre TypeScript',
  },
  {
    id: 5,
    titre: 'Apprendre Vue',
  },
]);
let nouvelleTacheId = 6;

function ajoutTodo() {
  todos.value.push({
    id: nouvelleTacheId++,
    titre: tache.value,
  });
  tache.value = '';
}

function suppTodo(id) {
  // Cela ne fonctionne pas !!
  // todos.value.filter((toto) => todo.id !== id);
  // Il faut réassigner le tableau :
  todos.value = todos.value.filter((todo) => todo.id !== id);
}
</script>

<style scoped lang="scss"></style>
