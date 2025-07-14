<template>
  <div class="flex flex-col items-center justify-center min-h-screen bg-gray-100">
    <!-- Portada -->
    <div
      class="bg-white shadow-lg rounded-lg p-10 cursor-pointer hover:shadow-2xl transition w-full max-w-md mx-4"
      @click="showModal = true"
    >
      <h1 class="font-bold text-2xl text-center">Welcome to My Gallery Art</h1>
      <p class="text-center text-gray-500 mt-2">Haz clic para ver la galería</p>
    </div>

    <!-- Modal de galería -->
    <div
      v-if="showModal"
      class="fixed inset-0 bg-black bg-opacity-60 flex items-center justify-center z-50"
    >
      <div class="bg-white rounded-lg p-4 sm:p-6 max-w-full sm:max-w-lg w-full relative flex flex-col items-center mx-2">
        <button
          class="absolute top-2 right-2 text-gray-500 hover:text-black text-2xl"
          @click="showModal = false"
        >
          &times;
        </button>
        <h2 class="text-xl font-bold mb-4 text-center">Galería</h2>
        <div class="flex items-center justify-center w-full">
          <button
            class="p-2"
            @click="prevImage"
            :disabled="currentIndex === 0"
          >
            <img
              src="/img/left-arrow.png"
              alt="Anterior"
              class="w-10 h-10 opacity-70 hover:opacity-100"
              :class="{ 'opacity-30 cursor-not-allowed': currentIndex === 0 }"
            />
          </button>
          <div class="flex-1 flex items-center justify-center">
            <img
              :src="images[currentIndex]"
              alt="Imagen de galería"
              class="max-w-full max-h-[60vh] sm:max-h-[400px] object-contain rounded shadow mx-2"
            />
          </div>
          <button
            class="p-2"
            @click="nextImage"
            :disabled="currentIndex === images.length - 1"
          >
            <img
              src="/img/right-arrow.png"
              alt="Siguiente"
              class="w-10 h-10 opacity-70 hover:opacity-100"
              :class="{ 'opacity-30 cursor-not-allowed': currentIndex === images.length - 1 }"
            />
          </button>
        </div>
        <div class="mt-2 text-center text-gray-500 text-sm">
          Imagen {{ currentIndex + 1 }} de {{ images.length }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const showModal = ref(false)
const images = [
  '/img/everyday.png',
  '/img/happy.png',
  '/img/zoo.png',
  '/img/flower.jpg',
  '/img/woman.jpg',
  '/img/bonfire.jpg'
]
const currentIndex = ref(0)

function nextImage() {
  if (currentIndex.value < images.length - 1) {
    currentIndex.value++
  }
}

function prevImage() {
  if (currentIndex.value > 0) {
    currentIndex.value--
  }
}

watch(showModal, (val) => {
  if (val) currentIndex.value = 0
})
</script>