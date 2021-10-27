<template>
    <header :class="{ 'scrolled-nav': scrolledNav }">
        <router-link to="/">
            <img class="logo" :src="logo" :alt="alt" id="logo">
        </router-link>
        <nav>
            <router-link class="nav-link" to="/">Home</router-link>
            <router-link class="nav-link" to="/Pedidos">Pedidos</router-link>
        </nav>
    </header>
</template>

<script>
export default {
    name: 'Navbar',
    props: ['logo', 'alt'],
    data() {
        return{
            scrolledNav: null,
        }
    },
    created(){
        window.addEventListener('scroll', this.updateScroll);
    },
    methods:{
        updateScroll(){
            const scrollPosition = window.scrollY;
            if (scrollPosition > 50) {
               this.scrolledNav = true;
               return;
            }
            this.scrolledNav = false;
        },
    }
}
</script>

<style lang="postcss" scoped>
header{
    @apply bg-transparent fixed flex justify-between items-center h-20 w-full;
    @apply md:px-5;
    transition: .3s;
    
}
.scrolled-nav{
    background-color: #222;
}
.logo{
    @apply w-16 px-2;
}
.nav-link{
    @apply text-xl px-3;
    color: #FCBA03;
    transition: .5s;
}
.nav-link:hover{
    color: #fff;
}
</style>