<script setup></script>

<template>
  <section class="hero">
    <!-- FUNDO VIDEO -->
    <div class="video-bg">
      <iframe
        src="https://www.youtube.com/embed/LMTftEixYUY?autoplay=1&mute=1&loop=1&controls=0&playlist=LMTftEixYUY&modestbranding=1&showinfo=0"
        frameborder="0"
        allow="autoplay; fullscreen"
        allowfullscreen
      ></iframe>
    </div>

    <!-- TEXTO -->
    <div class="content">
      <h2>
        Onde a paisagem vira <br />
        <span>inspiração</span>.
      </h2>

      <p>
        Explore paisagens, cores e luzes que inspiram novas histórias através da
        fotografia.
      </p>
    </div>

    <!-- IMAGEM HERO -->
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

  @media (max-width: 900px) {
    height: auto;
    padding: 1.5rem;
    flex-direction: column;
    gap: 2rem;
  }
}

/* Vídeo BG */
.video-bg {
  position: absolute;
  inset: 0;
  overflow: hidden;
  z-index: -1;

  iframe {
    width: 130%;
    height: 130%;
    position: absolute;
    top: -15%;
    left: -15%;
    object-fit: cover;
    filter: brightness(0.45);
    pointer-events: none;

    @media (max-width: 900px) {
      width: 180%;
      height: 180%;
      top: -40%;
      left: -40%;
      filter: brightness(0.35);
    }
  }
}

/* Conteúdo */
.content {
  z-index: 10;
  color: white;
  max-width: 45%;

  h2 {
    font-size: 3rem;
    line-height: 1.1;

    @media (max-width: 900px) {
      font-size: 2.2rem;
      text-align: center;
    }
  }

  span {
    font-size: 3.5rem;
    color: #ff2e63;
    font-weight: 700;

    @media (max-width: 900px) {
      font-size: 2.6rem;
    }
  }

  p {
    margin-top: 1rem;
    font-size: 1.2rem;
    opacity: 0.9;

    @media (max-width: 900px) {
      font-size: 1rem;
      text-align: center;
      max-width: 90%;
      margin: 0.8rem auto 0 auto;
    }
  }

  @media (max-width: 900px) {
    max-width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

/* Imagem */
.hero-img {
  width: 38vw;
  z-index: 10;
  filter: drop-shadow(0px 5px 15px rgba(0, 0, 0, 0.35));

  @media (max-width: 900px) {
    width: 75vw;
    max-width: 340px;
  }
}
</style>
