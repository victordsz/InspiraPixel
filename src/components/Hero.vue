<script setup></script>

<template>
  <section class="hero">
    <!-- Fundo YouTube -->
    <div class="video-bg">
      <iframe
        src="https://www.youtube.com/embed/LMTftEixYUY?autoplay=1&mute=1&loop=1&controls=0&playlist=LMTftEixYUY&modestbranding=1&showinfo=0"
        frameborder="0"
        allow="autoplay; fullscreen"
        allowfullscreen
      ></iframe>
    </div>

    <!-- Conteúdo -->
    <div class="content">
      <h2>Onde a paisagem vira <span>inspiração</span>.</h2>
      <p>
        Explore paisagens, cores e luzes que inspiram novas histórias através da
        fotografia.
      </p>
    </div>

    <img class="hero-img" src="../assets/fotografo.png" alt="Imagem ilustrativa" />
  </section>
</template>

<style scoped lang="scss">
.hero {
  position: relative;
  width: 100%;
  height: 90vh;
  padding: 2rem;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* FUNDO YOUTUBE */
.video-bg {
  position: absolute;
  inset: 0;
  overflow: hidden;
  z-index: -1;

  iframe {
    width: 120%;
    height: 120%;
    position: absolute;
    top: -10%;
    left: -10%;
    object-fit: cover;
    filter: brightness(0.45);
    pointer-events: none; /* impede interação com o vídeo */
  }
}

/* TEXTO */
.content {
  z-index: 10;
  color: white;
  max-width: 45%;

  h2 {
    font-size: 3rem;
    line-height: 1.1;
  }

  span {
    font-size: 3.5rem;
    color: #ff2e63;
    font-weight: 700;
  }

  p {
    margin-top: 1rem;
    font-size: 1.2rem;
    opacity: 0.9;
  }
}

/* IMAGEM */
.hero-img {
  width: 38vw;
  z-index: 10;
  filter: drop-shadow(0px 5px 15px rgba(0, 0, 0, 0.35));
}
</style>
