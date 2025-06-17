<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="container">
    <Clock />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Clock from './components/Clock.vue';

export default defineComponent({
  components: {
    Clock
  }
});
</script>

<style>
body {
  margin: 0;
  background: #E6E6FA;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
