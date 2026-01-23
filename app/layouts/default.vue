<script setup>
useHead({
    link: [
        {
            rel: "stylesheet",
            href: "https://site-ethmarks.vercel.app/common/ethmarks-rich.css",
        },
        {
            rel: "icon",
            href: "https://site-ethmarks.vercel.app/common/ethmarks.ico",
        },
    ],
    script: [
        {
            src: "https://site-ethmarks.vercel.app/common/ethmarks.wc.js",
            defer: "true",
        },
    ],
});
</script>

<template>
    <eth-header active="projects"></eth-header>
    <main>
        <slot />
    </main>
    <eth-footer src="https://github.com/ethmarks/projects"></eth-footer>
</template>
