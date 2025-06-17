<!-- src/components/Clock.vue -->
<template>
  <div class="clock">{{ time }}</div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted, onBeforeUnmount } from 'vue';

export default defineComponent({
  name: 'Clock',
  setup() {
    const time = ref<string>('');

    const updateTime = () => {
      const now = new Date();
      const hours = String(now.getHours()).padStart(2, '0');
      const minutes = String(now.getMinutes()).padStart(2, '0');
      const seconds = String(now.getSeconds()).padStart(2, '0');
      time.value = `${hours}:${minutes}:${seconds}`;
    };

    let intervalId: number;

    onMounted(() => {
      updateTime();
      intervalId = window.setInterval(updateTime, 1000);
    });

    onBeforeUnmount(() => {
      clearInterval(intervalId);
    });

    return {
      time
    };
  }
});
</script>

<style scoped>
.clock {
  font-size: 64px;
  font-weight: bold;
  color: #87CEFA;
  padding: 30px;
  background-color: #1e293b;
  border-radius: 16px;
  box-shadow: 0 0 20px #38bdf8aa;
  text-align: center;
}
</style>
