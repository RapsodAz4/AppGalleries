<template>
  <div class="gallery-wrapper">
    <!-- Portada -->
    <div
      class="gallery-card"
      @click="showModal = true"
    >
      <h1 class="gallery-title">Welcome to My Gallery of Pandas</h1>
      <p class="gallery-subtitle">Haz clic para ver la galería</p>
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
        <h2 class="text-xl font-bold mb-4 text-center">Galería de Pandas</h2>
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
              class="modal-image mx-2"
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
  '/img/panda1.png',
  '/img/panda2.png',
  '/img/panda3.png'
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

<style scoped>
/* Wrapper ahora usa grid para adaptarse al nuevo sistema de grid */
.gallery-wrapper {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1rem;
  align-items: start;
  width: 100%;
  padding: 1rem;
  box-sizing: border-box;
}

/* Tarjeta de galería */
.gallery-card {
  background: #ffffff;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.08), 0 4px 6px -2px rgba(0, 0, 0, 0.04);
  border-radius: 0.5rem;
  padding: 1.25rem;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

/* Efecto hover más sutil y consistente con el nuevo grid */
.gallery-card:hover {
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.2);
  transform: translateY(-4px);
}

.gallery-title {
  font-weight: 700;
  font-size: 1.125rem;
  margin-bottom: 0.5rem;
  color: #1f2937;
}

.gallery-subtitle {
  color: #6b7280;
  font-size: 0.875rem;
}

/* Imagen principal del modal: escala y límites responsivos */
.modal-image {
  max-width: 100%;
  max-height: 60vh;
  object-fit: contain;
  border-radius: 0.5rem;
  box-shadow: 0 6px 18px rgba(0,0,0,0.08);
}

/* Ajustes para pantallas más grandes */
@media (min-width: 640px) {
  .gallery-wrapper {
    gap: 1.25rem;
  }
  .modal-image {
    max-height: 400px;
  }
}

/* Opcional: estilos para el indicador de imagen dentro del modal */
.modal-counter {
  margin-top: 0.5rem;
  color: #6b7280;
  font-size: 0.875rem;
  text-align: center;
}
</style>