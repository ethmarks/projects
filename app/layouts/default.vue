<script setup>
const siteURL = useRuntimeConfig().public.siteURL; // "https://site-ethmarks.vercel.app/projects"
const route = useRoute();

const assetsURL = "https://site-ethmarks.vercel.app/common";
const sourceURL = "https://github.com/ethmarks/projects";

const pageTitle = computed(() => route.meta.title || "Projects");
const pageDesc = computed(
    () =>
        route.meta.desc ||
        "The projects collection of ethmarks's personal website",
);
const pageImg = computed(() => route.meta.img || "");

useSeoMeta({
    title: pageTitle,
    ogTitle: pageTitle,
    description: pageDesc,
    ogDescription: pageDesc,
});

if (pageImg.value) {
    useSeoMeta({
        ogImage: `${siteURL}${pageImg.value}`,
    });
}

useHead({
    htmlAttrs: { lang: "en-US" },
    link: [
        {
            rel: "canonical",
            href: siteURL + route.path,
        },
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
        {
            src: `https://site-ethmarks.vercel.app/_vercel/insights/script.js`,
            defer: true,
        },
        {
            innerHTML:
                "window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };",
        },
    ],
});
</script>

<template>
    <eth-header active="projects"></eth-header>
    <slot />
    <eth-footer :source="sourceURL"></eth-footer>
</template>
