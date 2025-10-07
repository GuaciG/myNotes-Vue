<script setup></script>

<template>
  <header class="header">
    <h1>My Notes App</h1>
    <nav>
      <ul class="nav-list">
        <li class="nav-item" v-for="link in ['Home', 'Notes']" :key="link">
          <router-link :to="link === 'Home' ? '/' : `/${link.toLowerCase()}`" class="link">{{ link }}</router-link>
        </li>
      </ul>
      <!-- <router-link to="/">Home</router-link>
      <router-link to="/notes">Notes</router-link> -->
    </nav>

  </header>
</template>

<style>
.header {
  background-color: #000022;
  color: white;
  padding: 30px;
  text-align: center;
  border-bottom: 2px solid #ccc;

  .title {
    font-size: 24px;
    margin: 0px;
    text-align: center;
  }
  .nav-list {
    display: flex;
    justify-content: space-around;
    list-style: none;
    padding: 0;
    .nav-item {
      font-size: 18px;

      .link {
        color: white;
        text-decoration: none;
      }

    }
  }
    
}
</style>