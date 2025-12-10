<script setup>
import { Icon } from "@iconify/vue";

defineProps({
  imagem: String,
  titulo: String,
});
</script>

<template>
  <div class="card">
    <img :src="imagem" :alt="titulo" />

    <div class="overlay">
      <h3>{{ titulo }}</h3>

      <div class="icons">
        <Icon icon="mdi:heart" width="26" height="26" />
        <Icon icon="mdi:download" width="26" height="26" />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card {
  position: relative;
  border-radius: 16px; 
  overflow: hidden;
  cursor: pointer;
  transition: 0.3s ease;
  background: #fff;
  box-shadow: 0 7px 20px rgba(0, 0, 0, 0.15); 
  break-inside: avoid; 

  img {
    width: 100%;
    height: auto;
    display: block;
    object-fit: cover;
    transition: 0.4s ease;
  }

  &:hover img {
    transform: scale(1.03);
    filter: brightness(0.55);
  }
}


.overlay {
  position: absolute;
  inset: 0;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.75), transparent);
  opacity: 0;
  transition: 0.3s ease;
}

.card:hover .overlay {
  opacity: 1;
}


.overlay h3 {
  color: #fff;
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 0.6rem;
  opacity: 0;
  transform: translateY(10px);
  transition: 0.3s ease;
}

.card:hover .overlay h3 {
  opacity: 1;
  transform: translateY(0);
}


.icons {
  display: flex;
  gap: 0.8rem;
  opacity: 0;
  transform: translateY(10px);
  transition: 0.3s ease;
}

.card:hover .icons {
  opacity: 1;
  transform: translateY(0);
}

.icons svg {
  color: rgba(255, 255, 255, 0.95);
  transition: 0.25s ease;
  backdrop-filter: blur(4px);
  padding: 6px;
  border-radius: 50%;
}

.icons svg:hover {
  color: #ff2e63;
  transform: scale(1.2);
}
</style>
