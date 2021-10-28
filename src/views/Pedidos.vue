<template>
    <section class="w-full h-screen pt-24 container mx-auto">
        <h1 class="text-8xl text-center">Pedidos</h1>
        <Dashboard />
    </section>
</template>

<script>
import Dashboard from '../components/Dashboard.vue'

export default {
    name: 'Pedidos',
    components: {
        Dashboard,
    }
}

</script>