<script setup>
import { Icon } from "@iconify/vue";
import { ref } from "vue";

const menuOpen = ref(false);
</script>

<template>
  <header>
    <img src="../assets/logo.png" alt="Logo" />

    <!-- Botão Hamburguer -->
    <button class="hamburger" @click="menuOpen = !menuOpen">
      <Icon
        v-if="!menuOpen"
        icon="material-symbols:menu-rounded"
        width="32"
        height="32"
      />
      <Icon
        v-else
        icon="material-symbols:close-rounded"
        width="32"
        height="32"
      />
    </button>

    <!-- NAV -->
    <nav :class="{ open: menuOpen }">
      <ul>
        <li>
          <a href="">
            <Icon icon="material-symbols:search" width="24" height="24" />
          </a>
        </li>

        <li><a href="">Início</a></li>
        <li><a href="">Galeria</a></li>
        <li><a href="">Favoritos</a></li>

        <li>
          <button class="btn-create">Criar conta</button>
        </li>

        <li>
          <button class="btn-login">
            <Icon icon="material-symbols:person-outline" width="24" height="24" />
          </button>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped lang="scss">
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 2rem;
  position: relative;

  img {
    height: 55px;
  }

  /* HAMBURGER BUTTON */
  .hamburger {
    background: none;
    border: none;
    cursor: pointer;
    display: none;
  }

  nav ul {
    display: flex;
    align-items: center;
    list-style: none;
    gap: 1.2rem;
  }

  a {
    text-decoration: none;
    color: black;
    font-weight: 500;
  }

  /* BOTÃO CRIAR CONTA */
  .btn-create {
    padding: 0.5rem 1rem;
    background: #c60000;
    color: #fff;
    border: none;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
    transition: 0.3s;

    &:hover {
      background: #950101;
    }
  }

  /* BOTÃO LOGIN */
  .btn-login {
    background: transparent;
    border: 2px solid #ccc;
    padding: 0.45rem 0.55rem;
    border-radius: 50%;
    cursor: pointer;
    transition: 0.3s;
    display: flex;

    &:hover {
      border-color: #c60000;
    }
  }
}

/* ----------- RESPONSIVO ----------- */
@media (max-width: 820px) {
  header {
    .hamburger {
      display: block;
    }

    nav {
      position: absolute;
      top: 100%;
      right: 0;
      background: white;
      width: 200px;
      padding: 1rem 0;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);

      opacity: 0;
      pointer-events: none;
      transform: translateY(-20px);
      transition: 0.3s;
    }

    nav.open {
      opacity: 1;
      pointer-events: auto;
      transform: translateY(0);
    }

    nav ul {
      flex-direction: column;
      gap: 1rem;
      padding: 0;
    }
  }
}
</style>
