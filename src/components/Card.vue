<script setup>
defineProps(["imagem"]);
</script>

<template>
    <div class="card">
        <button>💖</button>
        <img :src="imagem" alt="fotos" />
    </div>
</template>


<style scoped lang="scss">

.card {
    display: inline-block;
    /* ESSENCIAL para Masonry */
    width: 100%;
    margin-bottom: 20px;
    border-radius: 14px;
    overflow: hidden;
    background: #fff;
    position: relative;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
    transition: transform 0.2s ease, box-shadow 0.2s ease;

    &:hover {
        transform: translateY(-4px);
        box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
    }

    img {
        width: 100%;
        height: auto;
        /* ESSENCIAL — mantém alturas diferentes */
        display: block;
        border-radius: 12px;
    }

    button {
        position: absolute;
        top: 12px;
        right: 12px;
        background: #ffffffd8;
        border: none;
        border-radius: 50%;
        padding: 6px 10px;
        cursor: pointer;
        font-size: 1.1rem;
        transition: 0.2s ease;

        &:hover {
            background: #f2b63d;
            color: #fff;
            transform: scale(1.1);
        }
    }
}
</style>