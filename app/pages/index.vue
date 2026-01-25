<template>
    <main>
        <h1 id="site-heading">Projects</h1>
        <NuxtLink to="/fphf">
            <img
                class="card"
                src="/fphf_konsole.webp"
                alt="A screenshot of fphf being used in a terminal window against an abstract blue desktop wallaper. After running the command 'fphf', the terminal fills with status info as the process runs before eventually returning the string 'The SHA-256 hash of this sentence begins with b43c8b9.' and the hash 'b43c8b96f151033a566e148d45c43aa84ba153ff9407397f23d5eb43112bb5e1'"
                width="1920"
                height="1080"
                style="view-transition-name: img-fphf"
            />
        </NuxtLink>
    </main>
</template>

<style scoped>
h1 {
    margin-inline: auto;
    position: sticky;
    top: calc(var(--main-margin-top) + 0.2rem);
    z-index: 9999;
}

.card {
    width: 500px;
    height: auto;
    max-width: 100%;
}
</style>
