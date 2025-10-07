<script setup>
import { ref } from 'vue';
import { useNoteStore } from '../stores/note';

const noteStore = useNoteStore();

const handleSubmit = () => {
  noteStore.addNote(title.value);
  title.value = '';
};

const title = ref('');

</script>

<template>
  <form class="note-form" @submit.prevent="handleSubmit">
    <input 
      type="text" 
      v-model="title" 
      placeholder="Escribe tu nueva nota" 
      class="note-title" 
    />
    <button class="create-btn">+</button>
  </form>
</template>

<style>
.note-form {
  width: 400px;
  background-color: lightgreen;
  border: 3px solid darkblue;
  padding: 20px 30px;
  display: flex;
  justify-content: space-between;
  transition: all 0.3s ease;

  .note-title {
    background-color: transparent;
    border: none;
    font-size: 1.2rem;
    font-weight: bold;
  }

  .create-btn {
    background-color: green;
    color: white;
    width: 30px;
    height: 30px;
    font-size: 1.5rem;
    cursor: pointer;
    display: flex;
    align-items: center;
  }

  .create-btn:hover {
    background-color: darkgreen;
  }

  .create-btn:active {
    background-color: green;
  }
}

.note-form:hover {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  border-color: 3px solid black;
}

</style>