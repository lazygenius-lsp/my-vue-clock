<script setup lang="ts">
<<<<<<< HEAD
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
=======
import Clock from './components/Clock.vue'
import ColorTrailCursor from './components/ColorTrailCursor.vue'
>>>>>>> 6f5402c (Initial commit)
</script>

<template>
  <div class="container">
    <Clock />
<<<<<<< HEAD
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

=======
    <ColorTrailCursor />
  </div>
</template>

>>>>>>> 6f5402c (Initial commit)
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
