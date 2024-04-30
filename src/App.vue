<script setup>
import MainLayout from './layout/MainLayout.vue';
import Ducky from './components/Ducky.vue';
import Features from './components/Features.vue';
</script>

<template>
  <MainLayout>
    <section class="section-1 h-screen container grid grid-cols-2 justify-items-center items-center" id="hero">
      <div class="gap-4 flex flex-col">
        <h1 class="text-3xl font-bold">Mihai Romaniuc</h1>
        <h2 class="text-xl text-gray-500 italic ">3D Product Web Page example with
          <b class="font-bold">ThreeJS</b> and
          <b class="font-bold">WebGL</b>.
        </h2>
        <button
          class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow-md w-36">
          Know More </button>
      </div>
    </section>

    <section class="section-2 h-screen container grid grid-cols-2 justify-items-center items-center relative" id="card">
      <div class="absolute h-96 bg-yellow-300 -z-10 overflow-hidden" style="transform: rotate(15deg); width: 120vw;">
      </div>
      <div></div>
      <div class="rounded-lg bg-gray-100 border-dashed border-black border-4 p-6 shadow-md hover:skew-y-6 transition-all">
        <h5 class="mb-2 text-xl font-medium leading-tight text-neutral-800">
          Card title
        </h5>
        <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
      </div>
    </section>

    <section class="section-3 h-screen container grid grid-cols-2 justify-items-center items-center relative">
      <div class="absolute h-96 bg-blue-500 -z-10 overflow-hidden" style="transform: rotate(-15deg); width: 120vw;">
      </div>
      <div class="rounded-lg bg-gray-100 border-dashed border-black border-4 p-6 shadow-md hover:skew-y-6 transition-all">
        <h5 class="mb-2 text-xl font-medium leading-tight text-neutral-800">
          Card title
        </h5>
        <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
      </div>
    </section>

    <Features class="section-4 z-20"></Features>

    <section class="section-5 container flex flex-col " style="height: 70vh;" id="end">
      <h2 class="text-3xl text-center">Ducky</h2>
    </section>

    <Ducky />
  </MainLayout>
</template>
