<template>
    <p>
        &copy; {{ year }} Ng Zhe Kai. All Rights Reserved.
    </p>
</template>

<script>
export default {
    data() {
        return {
            year: new Date().getFullYear()
        }
    }
}
</script>

<style scoped>
p {
    color: rgba(0, 0, 0, 0.64);
}

@media (prefers-color-scheme: dark) {
    p {
        color: rgba(235, 235, 235, 0.64);
    }
}
</style>