<template>
  <transition name="fade" @after-leave="onFadeOutComplete">
    <div v-if="!isCompleted" class="loading-overlay">
      <div class="circle-container">
        <svg width="120" height="120" viewBox="0 0 120 120">
          <circle
            class="background-circle"
            cx="60"
            cy="60"
            r="50"
            fill="none"
            stroke="#e6e6e6"
            stroke-width="10"
          />
          <circle
            class="progress-circle"
            cx="60"
            cy="60"
            r="50"
            fill="none"
            :stroke="circleColor"
            stroke-width="10"
            stroke-dasharray="314.16"
            :stroke-dashoffset="314.16 - (314.16 * progress) / 100"
          />
        </svg>

        <div class="progress-text">{{ progress }}</div>
      </div>
      <p>{{ text }}</p>
    </div>
  </transition>

  <div v-if="isCompleted" class="completed-status">
    <div class="checkmark">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="50"
        height="50"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M20 6L9 17l-5-5"></path>
      </svg>
    </div>
    <p>Hoàn tất!</p>
  </div>
</template>
  
  <script setup>
import { ref, computed, onMounted } from "vue";

function hexToRgb(hex) {
  const bigint = parseInt(hex.replace("#", ""), 16);
  const r = (bigint >> 16) & 255;
  const g = (bigint >> 8) & 255;
  const b = bigint & 255;
  return { r, g, b };
}

function interpolateColor(startColor, endColor, factor) {
  const start = hexToRgb(startColor);
  const end = hexToRgb(endColor);
  const r = Math.round(start.r + factor * (end.r - start.r));
  const g = Math.round(start.g + factor * (end.g - start.g));
  const b = Math.round(start.b + factor * (end.b - start.b));
  return `rgb(${r}, ${g}, ${b})`;
}

const gradientColors = [
  { color: "#e74c3c", stop: 0 },
  { color: "#f39c12", stop: 50 },
  { color: "#2ecc71", stop: 100 },
];

const props = defineProps({
  text: {
    type: String,
    default: "Loading...",
  },
});

const progress = ref(0);

const circleColor = computed(() => {
  let currentColor = "#e74c3c";
  for (let i = 0; i < gradientColors.length - 1; i++) {
    const start = gradientColors[i];
    const end = gradientColors[i + 1];
    if (progress.value >= start.stop && progress.value <= end.stop) {
      const factor = (progress.value - start.stop) / (end.stop - start.stop);
      currentColor = interpolateColor(start.color, end.color, factor);
      break;
    }
  }
  return currentColor;
});

onMounted(() => {
  const interval = setInterval(() => {
    if (progress.value < 100) {
      progress.value += 1;
    } else {
      clearInterval(interval);
    }
  }, 10);
});
</script>
  
  <style>
@import url("https://fonts.googleapis.com/css2?family=Oswald:wght@400;500;600&display=swap");

.loading-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  color: white;
  font-size: 18px;
  font-family: "Oswald", sans-serif; /* Sử dụng font Oswald */
}

.circle-container {
  position: relative;
  width: 120px;
  height: 120px;
}

.background-circle {
  stroke: #e6e6e6;
}

.progress-circle {
  transform: rotate(-90deg);
  transform-origin: center;
  stroke-linecap: round;
  transition: stroke-dashoffset 0.3s;
}

.progress-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 36px;
  font-weight: 600;
  color: white;
  letter-spacing: 3px; 
}

.completed-status {
  text-align: center;
  font-size: 28px; 
  color: white;
}

.checkmark {
  width: 60px;
  height: 60px;
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #2ecc71;
  border-radius: 50%;
}

.checkmark svg {
  font-size: 48px; 
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
  