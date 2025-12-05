<script setup>
import Card from "./Card.vue";
</script>

<template>
    <section>

        <h2>Inspire-se</h2>

        <div class="cards-container">
            <Card imagem="URL1" />
            <Card imagem="URL2" />
            <Card imagem="URL3" />
            <Card imagem="URL4" />
        </div>

    </section>
</template>

<style scoped lang="scss">

.cards-container {
  column-count: 3;
  column-gap: 20px;
  padding: 1rem;

  > * {
    break-inside: avoid;
  }
}

@media (max-width: 900px) {
  .cards-container {
    column-count: 2;
  }
}

@media (max-width: 600px) {
  .cards-container {
    column-count: 1;
  }
}
h2{
    text-align: center;
    margin-bottom: 20px;
}

</style>