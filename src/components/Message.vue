<template>
    <section class="message-container">
        <p>{{ msg }}</p>
    </section>
</template>

<script>
export default {
    name: 'Message',
    props: {
        msg: String
    },
}
</script>

<style lang="postcss" scoped>
.message-container{
    @apply border-2;
    color: #004085;
    background-color: #cce5ff;
    border-color: #88daff;
    border-radius: 10px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
}
</style>