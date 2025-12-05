<script setup>
import { ref, watch, onMounted } from "vue";

const props = defineProps({
  imagem: String,
  id: Number // ID único do card para salvar no localStorage
});

// -------- ESTADOS --------
const curtido = ref(false);
const likes = ref(0);
const downloadOK = ref(false);

// -------- CARREGAR SALVO NO LOCALSTORAGE --------
onMounted(() => {
  const saved = JSON.parse(localStorage.getItem("likes-data")) || {};

  if (saved[props.id]) {
    curtido.value = saved[props.id].curtido;
    likes.value = saved[props.id].likes;
  }
});

// -------- SALVAR AUTOMATICAMENTE --------
watch([curtido, likes], () => {
  const saved = JSON.parse(localStorage.getItem("likes-data")) || {};

  saved[props.id] = {
    curtido: curtido.value,
    likes: likes.value
  };

  localStorage.setItem("likes-data", JSON.stringify(saved));
});

// -------- FUNÇÃO CURTIR --------
const toggleCurtida = () => {
  const wasLiked = curtido.value;
  curtido.value = !curtido.value;

  if (!wasLiked) {
    likes.value++;
  } else {
    likes.value--;
  }
};

// -------- FEEDBACK DO DOWNLOAD --------
const sucessoDownload = () => {
  downloadOK.value = true;
  setTimeout(() => (downloadOK.value = false), 800);
};
</script>

<template>
  <div class="card">
    <img :src="props.imagem" alt="Imagem Rio" />

    <!-- AÇÕES -->
    <div class="actions">

      <!-- BLOCO CURTIR -->
      <div class="action-item">

        <button class="icon-btn" @click="toggleCurtida">
          <!-- Ícone normal -->
          <svg
            v-if="!curtido"
            class="heart"
            width="26"
            height="26"
            viewBox="0 0 24 24"
            fill="none"
            stroke="white"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path
              d="M20.8 4.6a5.5 5.5 0 0 0-7.8 0L12 5.6l-1-1a5.5 5.5 0 0 0-7.8 7.8l1 1L12 21l7.8-7.8 1-1a5.5 5.5 0 0 0 0-7.8z"
            />
          </svg>

          <!-- Ícone curtido com pulse + brilho -->
          <svg
            v-else
            class="heart liked pulse glow"
            width="26"
            height="26"
            viewBox="0 0 24 24"
            fill="#ff3860"
            stroke="#ff3860"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path
              d="M20.8 4.6a5.5 5.5 0 0 0-7.8 0L12 5.6l-1-1a5.5 5.5 0 0 0-7.8 7.8l1 1L12 21l7.8-7.8 1-1a5.5 5.5 0 0 0 0-7.8z"
            />
          </svg>
        </button>

        <!-- CONTADOR COM ANIMAÇÃO - A RESOLVER  -->
        <span class="likes" :class="{ bounce: curtido }">
          {{ likes }}
        </span>

        <!-- Tooltip -->
        <div class="tooltip">
          {{ curtido ? "Descurtir" : "Curtir" }}
        </div>
      </div>

      <!-- BLOCO DOWNLOAD -->
      <div class="action-item">
        <a :href="props.imagem" download @click="sucessoDownload" class="icon-btn">
          <svg
            v-if="!downloadOK"
            width="26"
            height="26"
            viewBox="0 0 24 24"
            fill="none"
            stroke="white"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path d="M12 3v12"></path>
            <path d="m8 11 4 4 4-4"></path>
            <path d="M5 21h14"></path>
          </svg>

          <!-- Ícone -->
          <svg
            v-else
            width="26"
            height="26"
            viewBox="0 0 24 24"
            fill="none"
            stroke="#7CFC00"
            stroke-width="3"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="pulse"
          >
            <polyline points="20 6 9 17 4 12" />
          </svg>
        </a>

        <div class="tooltip">Baixar imagem</div>
      </div>

    </div>
  </div>
</template>

<style scoped lang="scss">

/* CARD */
.card {
  position: relative;
  width: 100%;
  aspect-ratio: 9 / 16;
  overflow: hidden;
  border-radius: 18px;
  background: #111;
  transition: 0.35s ease;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: .5s ease;
  }

  &:hover {
    img {
      transform: scale(1.1);
      filter: brightness(0.85);
    }
  }
}

/* AÇÕES */
.actions {
  position: absolute;
  bottom: 14px;
  left: 50%;
  transform: translateX(-50%);
  width: 88%;
  display: flex;
  justify-content: space-between;
}

/* Cada conjunto */
.action-item {
  position: relative;
  display: flex;
  align-items: center;
}

/* BOTÕES */
.icon-btn {
  width: 48px;
  height: 48px;
  border-radius: 14px;
  backdrop-filter: blur(8px);
  background: rgba(0, 0, 0, .45);
  border: 1px solid rgba(255, 255, 255, .22);
  display: flex;
  justify-content: center;
  align-items: center;
  transition: .25s ease;

  &:hover {
    background: rgba(255,255,255,.25);
    transform: scale(1.12);
  }
}

/* CURTIR - GLOW NÃO SEI SE VOU MANTER */
.glow {
  filter: drop-shadow(0 0 10px #ff3860);
}

/* CURTIR - PULSE */
.pulse {
  animation: pulse 0.4s ease forwards;
}

@keyframes pulse {
  0%   { transform: scale(1); }
  35%  { transform: scale(1.3); }
  70%  { transform: scale(0.9); }
  100% { transform: scale(1); }
}

/* CONTADOR - BOUNCE */
.bounce {
  animation: bounce 0.45s ease;
}

@keyframes bounce {
  0%   { transform: translateY(0); }
  40%  { transform: translateY(-6px); }
  100% { transform: translateY(0); }
}

/* TEXTOS & TOOLTIP */
.likes {
  margin-left: 8px;
  color: white;
  font-size: 1rem;
  font-weight: 600;
}

.tooltip {
  position: absolute;
  bottom: 58px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(15,15,15,.8);
  padding: 6px 12px;
  border-radius: 10px;
  font-size: .75rem;
  white-space: nowrap;
  opacity: 0;
  transition: .25s ease;
  backdrop-filter: blur(6px);
  border: 1px solid rgba(255,255,255,.15);
  pointer-events: none;
}

.action-item:hover .tooltip {
  opacity: 1;
  transform: translateX(-50%) translateY(-6px);
}

</style>
