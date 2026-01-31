<script setup>
const route = useRoute();

const src = route.meta.img;
const alt = route.meta.imgAlt;

const path = route.path.replace(/^\//, ""); // remove leading slash
const style = `view-transition-name: img-${path}`;
</script>

<template>
    <div class="hero">
        <img :src :alt decoding="sync" :style />
    </div>
</template>
