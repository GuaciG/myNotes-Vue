<script setup>

defineProps({
  note: Object
  
});

defineEmits(['delete-note']);

</script>

<template>
  <article class="note-card">
    <input type="text" 
      v-model="note.title" 
      class="card-title" 
      :class="{ 'marked': note.marked }"
    />
    <input type="checkbox" v-model="note.marked">
    <button @click="$emit('delete-note', note.id)" class="delete-btn">🗑️</button>

  </article>
</template>

<style>
.note-card {
  background-color: #ffff88;
  border: 2px solid #ccc;
  border-radius: 10px;
  padding: 20px 30px;
  width: 400px;
  display: flex;
  justify-content: space-between;
  transition: all 0.3s ease;
  gap: 10px;

  .card-title {
    font-size: 1.2rem;
    font-weight: bold;
    border: none;
    background-color: transparent;
    outline: none;
  }

  [type="checkbox"] {
    transform: scale(2) translateX(-2px);
    width: 20px;
    height: 20px;
    margin: auto 0;
    cursor: pointer;
  }

  .marked {
    text-decoration: line-through;
    color: #888;
  }

  .delete-btn {
  background: transparent;
  border: none;
  cursor: pointer;
  font-size: 2rem;
}

.delete-btn:hover {
  color: red;
}

  .note-card:hover {
    border: 3px solid black;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  }

  .note-card:has([type="checkbox"]:checked) {
    background-color: #88ff88;
    border-color: #00cc00;

    .card-title {
      text-decoration: line-through;
      color: #555;
      font-weight: 100;
    }
  }
}
</style>