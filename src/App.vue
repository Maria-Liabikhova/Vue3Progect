<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <div class="header">
      <h1 class="header__h1">ToEat</h1>
      <nav class="header__nav">
        <RouterLink class="header__link" to="/">Home</RouterLink>
        <RouterLink class="header__link" to="/about">About</RouterLink>
      </nav>
    </div>
  </header>
  <RouterView />
</template>

<style scoped>
.header__nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
  font-size: 1rem;
}
.header__link {
  margin-right: var(--space);
  color: var(--green);
  transition: all 0.3s ease;
}
.header__link:last-child {
  margin-right: 0;
}
nav a.router-link-exact-active {
  color: var(--color-text);
}
.header__h1 {
  color: var(--green);
  margin: 0;
  text-align: center;
}
</style>
