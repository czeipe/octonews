<template>
    <div class="wrapper">
        <h1 class="claim">Octonews</h1>
        <p class="subclaim">First paragraph in claim</p>
        <p class="subclaim">Second paragraph in course</p>
    </div>
</template>

<script>
export default {
    name: "Claim",
}
</script>

<style lang="scss" scoped>
    .claim{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
</style>
