<script setup>
import { Icon } from "@iconify/vue";
</script>

<template>
  <footer class="footer">
    <div class="footer-content">
      
      <!-- NEWSLETTER -->
      <div class="footer-newsletter">
        <h3></h3>
        <p>Assine e receba imagens em alta definição.</p>

        <div class="newsletter-input">
          <input type="email" placeholder="Digite seu e-mail" />
          <button>Inscrever</button>
        </div>

        <!-- SOCIAL ICONS -->
        <div class="social-icons">
          <a href="#">
            <Icon icon="ri:instagram-line" width="26" />
          </a>
          <a href="#">
            <Icon icon="mdi:facebook" width="26" />
          </a>
          <a href="#">
            <Icon icon="mdi:twitter" width="26" />
          </a>
          <a href="#">
            <Icon icon="mdi:youtube" width="26" />
          </a>
        </div>
      </div>

      <!-- ATENDIMENTO -->
      <div class="footer-column">
        <h4>Atendimento</h4>
        <ul>
          <li><a href="#">Fale Conosco</a></li>
          <li><a href="#">Perguntas Frequentes</a></li>
        </ul>
      </div>

      <!-- INSTITUCIONAL -->
      <div class="footer-column">
        <h4>Institucional</h4>
        <ul>
          <li><a href="#">Sobre Nós</a></li>
          <li><a href="#">Política de Privacidade</a></li>
          <li><a href="#">Trabalhe Conosco</a></li>
          
        </ul>
      </div>
    </div>

    <div class="footer-divider"></div>

    <p class="footer-copy">© 2025 Inspirapixel — Todos os direitos reservados.</p>
  </footer>
</template>

<style scoped lang="scss">
.footer {
  width: 100%;
  padding: 3rem 2rem;
  background: #fafafa;
  color: #333;
  border-top: 1px solid #e5e5e5;

  display: flex;
  flex-direction: column;
  gap: 2rem;

  .footer-content {
    display: flex;
    flex-direction: column;
    gap: 2.5rem;

    @media (min-width: 768px) {
      flex-direction: row;
      justify-content: space-between;
      align-items: flex-start;
    }
  }

  /* NEWSLETTER */
  .footer-newsletter {
    flex: 1;

    p {
      font-size: 0.95rem;
      margin-bottom: 1rem;
      color: #666;
    }

    .newsletter-input {
      display: flex;
      gap: 0.6rem;
      margin-top: 0.5rem;

      input {
        flex: 1;
        padding: 0.75rem;
        border: 1px solid #ccc;
        border-radius: 6px;
        outline: none;
        font-size: 0.95rem;

        &:focus {
          border-color: #c60000;
        }
      }

      button {
        background: #c60000;
        border: none;
        padding: 0.75rem 1.2rem;
        border-radius: 6px;
        font-weight: 600;
        cursor: pointer;
        transition: 0.2s;

        &:hover {
          background: #c60000;
        }
      }
    }

    /* SOCIAL ICONS */
    .social-icons {
      margin-top: 1.5rem;
      display: flex;
      gap: 1rem;

      a {
        color: #444;
        transition: 0.2s;

        &:hover {
          color: #c60000;
          transform: translateY(-3px);
        }
      }
    }
  }

  /* COLUNAS PADRÕES */
  .footer-column {
    flex: 0.5;

    h4 {
      font-family: "Poppins", sans-serif;
      font-size: 1rem;
      margin-bottom: 1rem;
      font-weight: 600;
      color: #2d2d2d;
    }

    ul {
      padding: 0;
      display: flex;
      flex-direction: column;
      gap: 0.7rem;

      li {
        list-style: none;

        a {
          text-decoration: none;
          color: #555;
          font-size: 0.95rem;
          transition: 0.2s;

          &:hover {
            color: #c60000;
          }
        }
      }
    }
  }

  .footer-divider {
    width: 100%;
    height: 1px;
    background: #e5e5e5;
    margin-top: 1rem;
  }

  .footer-copy {
    text-align: center;
    font-size: 0.85rem;
    color: #777;
  }
}
</style>