<template>
    <footer class="footer">
        <h1 class="text">Make Your Burguer &copy; 2021</h1>
    </footer>
</template>

<script>
export default{
    name: 'Footer',
}
</script>

<style lang="postcss" scoped>
.footer{
    @apply flex justify-center items-center h-16;
    background-color: #222;
}
.text{
    @apply text-xl;
    color: #FCBA03;
}
</style>