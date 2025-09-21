<template>
  <div>
    <HeroSection />
  </div>
  <div class="galleries-container">
     <div class="galleries-grid">
    <Gallery />
  <GalleryPandas />
</div>
</div>
</template>

<script>
import GalleryPandas from '~/components/GalleryPandas.vue';
</script>

<style scoped>
.galleries-container {
padding: 2rem 1rem;
background-color: #f3f4f6;
}

.galleries-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
gap: 2rem;
max-width: 1200px;
margin: 0 auto;
}

/* Responsive adjustments */
@media (max-width: 768px) {
.galleries-grid {
grid-template-columns: 1fr;
gap: 1.5rem;
}

.galleries-container {
padding: 1rem 0.5rem;
}
}

@media (min-width: 1400px) {
.galleries-grid {
grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
}
}
</style>