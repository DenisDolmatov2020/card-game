<script setup lang="ts">
interface Props {
  isFlip: boolean;
}

defineProps<Props>();
</script>

<template>
  <button class="button">
    <span></span>
    <span></span>
    {{ isFlip ? 'Close' : 'Open' }}
  </button>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;300;400;500;600;700;800;900&display=swap');

.button {
  cursor: pointer;
  bottom: 20px;
  right: 20px;
  position: absolute;
  padding: 16px 30px;
  font-size: 1.5rem;
  color: #1e9bff;
  border: none;
  text-shadow: 0 0 15px #1e9bff;
  text-decoration: none;
  text-transform: uppercase;
  letter-spacing: 0.1rem;
  transition: 0.5s;
  z-index: 1;
  border-radius: 20px;
}

.button:hover {
  color: #fff;
  border: 2px solid rgba(0, 0, 0, 0);
  box-shadow: 0 0 0px #1e9bff;
}

.button::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #1e9bff;
  z-index: -1;
  transform: scale(0);
  transition: 0.5s;
}

.button:hover::before {
  transform: scale(1);
  transition-delay: 0.5s;
  box-shadow: 0 0 10px #1e9bff,
  0 0 30px #1e9bff,
  0 0 60px #1e9bff;
}

.button span {
  position: absolute;
  background: #1e9bff;
  pointer-events: none;
  border-radius: 2px;
  box-shadow: 0 0 10px #1e9bff,
  0 0 10px #1e9bff,
  0 0 20px #1e9bff,
  0 0 40px #1e9bff,
  0 0 600px #1e9bff;
  transition: 0.5s ease-in-out;
  transition-delay: 0.25s;
}

.button:hover span {
  opacity: 0;
  transition-delay: 0s;
}

.button span:nth-child(1) {
  width: 20px;
  height: 4px;
}

.button:hover span:nth-child(1) {
  transform: translateX(0);
}

.button span:nth-child(2) {
  width: 4px;
  height: 20px;
}

.button:hover span:nth-child(1) {
  transform: translateY(0);
}

.button span:nth-child(1) {
  top: calc(30% - 2px);
  left: -30px;
  transform-origin: left;
}

.button:hover span:nth-child(1) {
  left: 30%;
}

.button span:nth-child(2) {
  left: calc(30% - 2px);
  top: -30px;
  transform-origin: top;
}

.button:hover span:nth-child(2) {
  top: 30%;
}
</style>