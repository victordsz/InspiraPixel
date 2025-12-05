<script setup> 
import { Icon } from "@iconify/vue";
</script>

<template>
  <header>
    <img src="../assets/logo.png" alt="Logo" />

    <nav>
      <ul>
        <!-- BUSCA -->
        <li>
          <a href="">
            <Icon icon="material-symbols:search" width="24" height="24" />
          </a>
        </li>

        <!-- LINKS -->
        <li><a href="">Início</a></li>
        <li><a href="">Galeria</a></li>
        <li><a href="">Favoritos</a></li>

        <!-- BOTÕES DE CONTA -->
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

  img {
    height: 55px;
  }

  ul {
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
    background: #f2b63d;
    color: #fff;
    border: none;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
    transition: 0.3s;

    &:hover {
      background: #d99c2f;
    }
  }

  /* BOTÃO LOGIN COM ÍCONE */
  .btn-login {
    background: transparent;
    border: 2px solid #ccc;
    padding: 0.45rem 0.55rem;
    border-radius: 50%;
    cursor: pointer;
    transition: 0.3s;

    display: flex;
    justify-content: center;
    align-items: center;

    &:hover {
      border-color: #f2b63d;
    }
  }
}
</style>