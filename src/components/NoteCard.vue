<script setup>
defineProps({
  note: Object
  
});
</script>

<template>
  <article class="note-card">
    <input type="text" v-model="note.title" class="card-title" />
    <input type="checkbox" v-model="note.marked">

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