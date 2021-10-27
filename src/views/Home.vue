<template>
    <Banner />
    <section class="container mx-auto h-screen">
        <p class="text-5xl text-center">Monte seu Burger:</p>
        <BurgerForm />
    </section>
</template>

<script>
import Banner from '../components/Banner.vue'
import BurgerForm from '../components/BurgerForm.vue'

export default {
    name: 'Home',
    components: {
        Banner,
        BurgerForm,
    }
}
</script>