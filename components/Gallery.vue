<template>
  <div class="gallery-wrapper">
    <!-- Portada -->
    <div
      class="gallery-card"
      @click="showModal = true"
    >
      <h1 class="gallery-title">Welcome to My Gallery Art</h1>
      <p class="gallery-subtitle">Haz clic para ver la galería</p>
    </div>

    <!-- Modal de galería -->
    <div
      v-if="showModal"
      class="gallery-modal"
    >
      <div class="gallery-modal-content">
        <button
          class="gallery-close-btn"
          @click="showModal = false"
        >
          &times;
        </button>
        <h2 class="gallery-modal-title">Galería</h2>
        <div class="gallery-navigation">
          <button
            class="gallery-nav-btn gallery-nav-prev"
            @click="prevImage"
            :disabled="currentIndex === 0"
          >
            <img
              src="/img/left-arrow.png"
              alt="Anterior"
              class="gallery-arrow"
              :class="{ 'gallery-arrow-disabled': currentIndex === 0 }"
            />
          </button>
          <div class="gallery-image-container">
            <img
              :src="images[currentIndex]"
              alt="Imagen de galería"
              class="gallery-image"
            />
          </div>
          <button
            class="gallery-nav-btn gallery-nav-next"
            @click="nextImage"
            :disabled="currentIndex === images.length - 1"
          >
            <img
              src="/img/right-arrow.png"
              alt="Siguiente"
              class="gallery-arrow"
              :class="{ 'gallery-arrow-disabled': currentIndex === images.length - 1 }"
            />
          </button>
        </div>
        <div class="gallery-counter">
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

<style scoped>
.gallery-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  padding: 1rem;
}

.gallery-card {
  background: white;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  border-radius: 0.5rem;
  padding: 2rem;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
  max-width: 400px;
  text-align: center;
}

.gallery-card:hover {
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  transform: translateY(-2px);
}

.gallery-title {
  font-weight: bold;
  font-size: 1.25rem;
  margin-bottom: 0.5rem;
  color: #1f2937;
}

.gallery-subtitle {
  color: #6b7280;
  font-size: 0.875rem;
}

/* Modal Styles */
.gallery-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.6);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 50;
  backdrop-filter: blur(2px);
}

.gallery-modal-content {
  background: white;
  border-radius: 0.75rem;
  padding: 1.5rem;
  width: 100%;
  max-width: 90vw;
  max-height: 90vh;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 1rem;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

.gallery-close-btn {
  position: absolute;
  top: 0.75rem;
  right: 0.75rem;
  color: #6b7280;
  font-size: 2rem;
  line-height: 1;
  background: none;
  border: none;
  cursor: pointer;
  transition: color 0.2s ease;
  z-index: 10;
}

.gallery-close-btn:hover {
  color: #1f2937;
}

.gallery-modal-title {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
  text-align: center;
  color: #1f2937;
}

.gallery-navigation {
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
  gap: 1rem;
  width: 100%;
  max-width: 800px;
}

.gallery-nav-btn {
  padding: 0.5rem;
  background: none;
  border: none;
  cursor: pointer;
  transition: all 0.2s ease;
  border-radius: 0.5rem;
}

.gallery-nav-btn:hover:not(:disabled) {
  background-color: #f3f4f6;
}

.gallery-nav-btn:disabled {
  cursor: not-allowed;
}

.gallery-image-container {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 300px;
}

.gallery-image {
  max-width: 100%;
  max-height: 60vh;
  object-fit: contain;
  border-radius: 0.5rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.gallery-arrow {
  width: 2.5rem;
  height: 2.5rem;
  opacity: 0.7;
  transition: opacity 0.2s ease;
}

.gallery-arrow:hover {
  opacity: 1;
}

.gallery-arrow-disabled {
  opacity: 0.3;
}

.gallery-counter {
  margin-top: 1rem;
  text-align: center;
  color: #6b7280;
  font-size: 0.875rem;
}

/* Responsive Design */
@media (max-width: 640px) {
  .gallery-modal-content {
    padding: 1rem;
    margin: 0.5rem;
  }

  .gallery-navigation {
    gap: 0.5rem;
  }

  .gallery-arrow {
    width: 2rem;
    height: 2rem;
  }

  .gallery-image {
    max-height: 50vh;
  }

  .gallery-modal-title {
    font-size: 1.25rem;
    margin-bottom: 1rem;
  }
}

@media (max-width: 480px) {
  .gallery-navigation {
    grid-template-columns: 1fr;
    grid-template-rows: auto 1fr auto;
    gap: 1rem;
  }

  .gallery-nav-prev {
    grid-row: 3;
    justify-self: start;
  }

  .gallery-nav-next {
    grid-row: 3;
    justify-self: end;
  }

  .gallery-image-container {
    grid-row: 2;
    grid-column: 1;
  }
}
</style>