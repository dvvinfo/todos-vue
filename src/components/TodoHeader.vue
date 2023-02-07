<template>
  <header>
    <nav class="container">
      <div class="branding">
        <img src="../assets/logo.svg" alt="logo" />
        <h1>Vue Todo</h1>
      </div>
      <ul class="nav-routes">
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { RouterLink } from "vue-router";
</script>

<style lang="scss" scoped>
header {
  background-color: #f1f1f1;
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 25px 16px;
    .branding {
    flex-shrink: 0;
      display: flex;
      align-items: center;
      gap: 8px;
      max-width: 200px;
      width: 100%;
      img {
        max-width: 50px;
      }
      h1 {
        font-size: 24px;
      }
    }
    .nav-routes {
      display: flex;
      justify-content: flex-end;
      gap: 12px;
      list-style: none;
      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}
</style>
