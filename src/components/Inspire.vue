<script setup>
import Card from "./Card.vue";
const imagensRio = [
 "https://i.pinimg.com/736x/6f/36/e0/6f36e093219b12bb8c61785aa7d61a73.jpg",
 "https://upload.wikimedia.org/wikipedia/commons/thumb/f/fc/Vista_do_Morro_Dona_Marta.jpg/1200px-Vista_do_Morro_Dona_Marta.jpg",
 "https://i.ytimg.com/vi/IAmF6bqIU60/maxresdefault.jpg?rs=AOn4CLBtQWL_2qAIwr2qYI630M-2w1VcxQ&sqp=-oaymwEmCIAKENAF8quKqQMa8AEB-AH-CYAC0AWKAgwIABABGFYgYihlMA8%3D",
 "https://riodejaneirobycariocas.com/wp-content/uploads/2018/10/eppinghaus-arpoador00-min-jpg.webp",
 "https://www.zapimoveis.com.br/blog/wp-content/uploads/2024/04/lagoa-rodrigo-de-freitas.jpg",
 "https://admin.passeiorio.com.br/wp-content/uploads/2024/10/floresta-da-tijuca.jpg",
];
</script>

<template>
  <section class="inspire">
    <h2>Inspire-se</h2>

    <div class="cards-container">
    
      <Card v-for="(img, index) in imagensRio" :key="index" :imagem="img" />
    </div>
  </section>
</template>

<style scoped lang="scss">
.cards-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); 
  gap: 20px;
  width: 100%;
  margin-top: 20px;
}

@media (max-width: 900px) {
  .cards-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .cards-container {
    grid-template-columns: repeat(1, 1fr);
  }
}

h2{
  font-size: 2rem;
  margin-bottom: 1rem;
  color: #333;
  display: flex;
  justify-content: center;
}
</style>