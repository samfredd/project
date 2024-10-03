<template>
    <div class="shimmer-loader">
        <div class="shimmer" v-for="n in 10" :key="n"></div>
    </div>
</template>

<style scoped>
.shimmer-loader {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
}

.shimmer {
    background: linear-gradient(90deg, rgba(255, 255, 255, 0.2) 0%, rgba(255, 255, 255, 0.5) 50%, rgba(255, 255, 255, 0.2) 100%);
    height: 200px;
    /* Adjust height according to your needs */
    border-radius: 16px;
    animation: shimmer 1.5s infinite;
}

@keyframes shimmer {
    0% {
        background-position: -100px 0;
    }

    100% {
        background-position: 100px 0;
    }
}
</style>
