<template>
  <div class="trail-cursor">
    <div
      v-for="(circle, index) in circles"
      :key="circle.id"
      class="trail-dot"
      :style="{
        left: circle.x + 'px',
        top: circle.y + 'px',
        backgroundColor: circle.color,
        opacity: circle.opacity,
        transform: 'scale(' + circle.scale + ')'
      }"
    ></div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

interface TrailDot {
  id: number
  x: number
  y: number
  color: string
  opacity: number
  scale: number
}

const circles = ref<TrailDot[]>([])
let idCounter = 0

const colors = [
  '#add8e6', '#e0ffff', '#20b2aa',
  '#87cefa', '#afeeee', '#0000cd'
]

function getRandomColor() {
  return colors[Math.floor(Math.random() * colors.length)]
}

function createCircle(x: number, y: number) {
  circles.value.push({
    id: idCounter++,
    x,
    y,
    color: getRandomColor(),
    opacity: 1,
    scale: 1
  })
}

function animate() {
  for (let i = 0; i < circles.value.length; i++) {
    const c = circles.value[i]
    c.opacity -= 0.03
    c.scale -= 0.01
  }

  circles.value = circles.value.filter(c => c.opacity > 0)

  requestAnimationFrame(animate)
}

function handleMouseMove(e: MouseEvent) {
  createCircle(e.clientX, e.clientY)
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
  animate()
})

onUnmounted(() => {
  window.removeEventListener('mousemove', handleMouseMove)
})
</script>

<style scoped>
.trail-cursor {
  position: fixed;
  pointer-events: none;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 9999;
  overflow: hidden;
}

.trail-dot {
  position: absolute;
  width: 16px;
  height: 16px;
  clip-path: polygon(
    50% 0%,
    61% 35%,
    98% 35%,
    68% 57%,
    79% 91%,
    50% 70%,
    21% 91%,
    32% 57%,
    2% 35%,
    39% 35%
  );
  transition: all 0.1s linear;
}
</style>
