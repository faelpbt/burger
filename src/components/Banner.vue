<template>
    <section class="banner">
        <h1 class="text">Make Your Burger</h1>
    </section>
</template>

<script>
    export default {
        name: 'Banner',
    }
</script>

<style lang="postcss" scoped>
.banner{
    @apply flex items-center justify-start;
    height: 900px;
    background-image: url('/img/burger.jpg');
    background-position: 0 -170px;
    background-size: cover;
}
.text{
    @apply text-7xl text-center text-white px-8
    py-8 rounded-r-full;
    background-color: #222;
}
</style>