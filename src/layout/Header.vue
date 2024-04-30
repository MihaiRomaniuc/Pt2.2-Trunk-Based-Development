<script setup>
import { ArrowUpRightIcon } from '@heroicons/vue/24/solid';
</script>

<template>
    <header class="fixed w-full">
        <nav class="bg-blue-500 text-white px-4 lg:px-6 py-2.5">
            <div class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl">
                <a href="https://flowbite.com" class="flex items-center">
                    <img src="../assets/duck.svg" class="mr-3 h-6 sm:h-9 invert" alt="Duck Logo" />
                    <span class="self-center text-xl font-semibold whitespace-nowrap dark:text-white">Ducky WebGL</span>
                </a>

                <div class="flex items-center lg:order-2">
                    <a href="#"
                        class="text-white hover:ring-4 hover:ring-gray-300 font-medium rounded-lg text-sm px-4 lg:px-5 py-2 lg:py-2.5 mr-2 flex flex-nowrap">
                        <span class="pr-1">Portfolio</span>
                        <ArrowUpRightIcon class="w-4" />
                    </a>
                </div>
            </div>
        </nav>
    </header>
</template>
