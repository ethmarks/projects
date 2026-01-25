<script setup>
const assetsURL = "https://site-ethmarks.vercel.app/common";

const title = "ethmarks/projects";
const description = "The projects collection of ethmarks's personal website";
const sourceURL = "https://github.com/ethmarks/projects";

useHead({
    link: [
        {
            rel: "icon",
            href: `${assetsURL}/ethmarks.ico`,
            type: "image/x-icon",
        },
        {
            rel: "stylesheet",
            href: `${assetsURL}/ethmarks-rich.css`,
        },
    ],
    script: [
        {
            src: `${assetsURL}/ethmarks.wc.js`,
            defer: true,
        },
        {
            src: `${assetsURL}/overflow.js`,
            defer: true,
        },
    ],
});
</script>

<template>
    <eth-header active="projects"></eth-header>
    <slot />
    <eth-footer :source="sourceURL"></eth-footer>
</template>
