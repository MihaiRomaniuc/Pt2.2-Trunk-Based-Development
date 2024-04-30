<script setup>
import Header from './Header.vue';
import Footer from './Footer.vue';
</script>

<template class="bg-slate-50">
    <Header></Header>
    <main class="overflow-hidden ">
        <div class="container mx-auto flex flex-col items-center gap-4 ">
            <slot />
        </div>
    </main>
    <Footer></Footer>
</template>
