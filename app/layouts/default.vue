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
    ],
});
</script>

<template>
    <eth-header active="projects"></eth-header>
    <slot />
    <eth-footer :source="sourceURL"></eth-footer>
</template>

<style>
:root {
    --main-width: 1200px;
}
.frontmatter,
.heading,
main > article {
    width: 850px;
    margin-inline: auto;
}
.hero {
    width: 1000px;
    margin-inline: auto;
}
.hero img {
    border: var(--border-standard-2px);
}
</style>
