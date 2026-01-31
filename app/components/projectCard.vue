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
    title: {
        type: String,
        required: true,
    },
    desc: {
        type: String,
        required: true,
    },
});
const style = `view-transition-name: img-${props.id}`;

const config = useRuntimeConfig();
const base = config.app.baseURL.replace(/\/$/, "");
const src = `${base}${props.img}`;
</script>

<template>
    <div class="projectCard staggered">
        <NuxtLink :to="href">
            <img class="card" :src :alt="props.alt" :style />
        </NuxtLink>
        <div class="info">
            <h2>{{ props.title }}</h2>
            <p>{{ props.desc }}</p>
        </div>
    </div>
</template>

<style scoped>
.projectCard {
    --column-one: 3fr;
    --column-two: 2fr;
    display: grid;
    grid-template-columns: var(--column-one) var(--column-two);
    gap: var(--spacing-lg);
}
.projectCard:nth-child(even) {
    grid-template-columns: var(--column-two) var(--column-one);
}

@media (max-width: 768px) {
    .projectCard {
        display: flex;
        flex-direction: column;
        gap: 0;
        padding: var(--spacing-xs);
    }
    .info {
        order: -1;
    }
    h2 {
        margin-block: 0;
    }
    p {
        margin-block: 0;
    }
    a {
        max-width: 90%;
    }
    .projectCard:nth-child(even) a {
        margin-left: auto;
    }
}

.projectCard:nth-child(even) img {
    animation-name: cardEntranceRight;
}
.projectCard:nth-child(even) .info {
    text-align: right;
}
.projectCard:nth-child(even) h2 {
    animation-name: h2EntranceLeft;
}
@media (min-width: 769px) {
    .projectCard:nth-child(even) .info {
        order: -1;
    }
}
h2 {
    color: var(--color-accent);
    animation: h2EntranceRight 1s calc(0.3s + var(--child-animation-delay) * 6)
        ease both;
}
p {
    animation: descEntrance 1s calc(0.5s + var(--child-animation-delay) * 6)
        ease both;
}

img {
    width: 100%;
    height: auto;
    max-width: 100%;
    object-fit: cover;
    border-radius: var(--radius-xl);
    border: var(--border-standard-2px);
    animation: cardEntranceLeft 1s calc(var(--child-animation-delay) * 6) ease
        both;
}

a {
    display: block;
    width: 100%;
    height: 100%;
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
@keyframes h2EntranceRight {
    0% {
        opacity: 0;
        transform: translateX(100px);
        text-shadow:
            00px 0 3px color-mix(in srgb, var(--color-accent) 50%, black),
            20px 0 3px color-mix(in srgb, var(--color-accent) 60%, black),
            40px 0 3px color-mix(in srgb, var(--color-accent) 50%, black),
            80px 0 3px color-mix(in srgb, var(--color-accent) 40%, black);
    }

    60% {
        text-shadow:
            0px 0 1px color-mix(in srgb, var(--color-accent) 50%, black),
            1px 0 1px color-mix(in srgb, var(--color-accent) 60%, black),
            2px 0 1px color-mix(in srgb, var(--color-accent) 50%, black),
            4px 0 1px color-mix(in srgb, var(--color-accent) 40%, black);
    }

    100% {
        opacity: 1;
        transform: translateX(0);
        text-shadow:
            0px 0 1px transparent,
            1px 0 1px transparent,
            2px 0 1px transparent,
            4px 0 1px transparent;
    }
}
@keyframes h2EntranceLeft {
    0% {
        opacity: 0;
        transform: translateX(-100px);
        text-shadow:
            00px 0 3px color-mix(in srgb, var(--color-accent) 50%, black),
            -20px 0 3px color-mix(in srgb, var(--color-accent) 60%, black),
            -40px 0 3px color-mix(in srgb, var(--color-accent) 50%, black),
            -80px 0 3px color-mix(in srgb, var(--color-accent) 40%, black);
    }

    60% {
        text-shadow:
            0px 0 1px color-mix(in srgb, var(--color-accent) 50%, black),
            -1px 0 1px color-mix(in srgb, var(--color-accent) 60%, black),
            -2px 0 1px color-mix(in srgb, var(--color-accent) 50%, black),
            -4px 0 1px color-mix(in srgb, var(--color-accent) 40%, black);
    }

    100% {
        opacity: 1;
        transform: translateX(0);
        text-shadow:
            0px 0 1px transparent,
            -1px 0 1px transparent,
            -2px 0 1px transparent,
            -4px 0 1px transparent;
    }
}

@keyframes descEntrance {
    from {
        opacity: 0;
        transform: translateY(30px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>
