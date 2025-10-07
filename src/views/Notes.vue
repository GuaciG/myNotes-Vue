<script setup>
import { onMounted } from 'vue';
import CreateNote from '../components/CreateNote.vue';
import HeaderComponent from '../components/HeaderComponent.vue';
import NoteCard from '../components/NoteCard.vue';
import { useNoteStore } from '../stores/note';


const noteStore = useNoteStore();

onMounted(async () => {
  await noteStore.getNotes()
});

</script>

<template>
  <HeaderComponent />
  <section id="notes-page">
    <h2>Notes</h2>

    <h2 v-if="noteStore.loading">Cargando...</h2>
    <h2 v-else-if="noteStore.error">La petición a la API ha ido mal</h2>
    <ul v-else class="note-list">
      <li class="title">
        <CreateNote />
      </li>
      <li v-for="note in noteStore.notes" :key="note.id" class="title">
          <NoteCard 
            :note="note"
            @delete-note="noteStore.deleteNote"
          />
      </li>
      <li v-if="noteStore.notes.length === 0" class="empty-msg">
        <h2>No hay notas que mostrar. Crea tu primera nota!</h2>
      </li>
    </ul>
  </section>
</template>

<style>
#notes-page {
  padding: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;

  .title {
      font-size: 24px;
      margin-bottom: 20px;
      text-align: center;
    }

  .note-list {
    background-image: url('/assets/cork.jpg');
    border: 10px solid brown;
    width: 70%;
    min-width: 450px;
    padding: 30px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;

    .empty-msg {
      font-size: 1.5rem;
      text-align: center;
    }
  }  
}
</style>