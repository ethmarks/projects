<script setup>
const props = defineProps({
    id: {
        type: String,
        required: true,
    },
    href: {
        type: String,
        required: true,
    },
    img: {
        type: String,
        required: true,
    },
    alt: {
        type: String,
        required: true,
    },
});
const style = `view-transition-name: img-${props.id}`;
</script>

<template>
    <NuxtLink :to="href">
        <img class="card" :src="props.img" :alt="props.alt" :style />
    </NuxtLink>
</template>

<style>
.card {
    width: 500px;
    height: auto;
    max-width: 100%;
    border-radius: var(--radius-md);
    animation: cardEntranceLeft 1s ease forwards;
}

a {
    width: max-content;
}

@keyframes cardEntranceLeft {
    0% {
        clip-path: xywh(0 0 0 30% round var(--radius-md));
    }
    60% {
        clip-path: xywh(0 0 100% 40% round var(--radius-md));
    }
    100% {
        clip-path: xywh(0 0 100% 100% round var(--radius-md));
    }
}

@keyframes cardEntranceRight {
    0% {
        clip-path: xywh(100% 0 0 30% round var(--radius-md));
    }
    60% {
        clip-path: xywh(0 0 100% 40% round var(--radius-md));
    }
    100% {
        clip-path: xywh(0 0 100% 100% round var(--radius-md));
    }
}
</style>
