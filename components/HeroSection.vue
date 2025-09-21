<template>
  <!-- Hero Section -->
  <section class="bg-gradient-to-r from-indigo-500 to-purple-600 text-white py-20">
    <div class="container mx-auto px-4 flex flex-col md:flex-row items-center">
      <!-- Contenido de texto -->
      <div class="md:w-1/2 mb-10 md:mb-0">
        <h1 class="text-4xl md:text-5xl font-bold mb-4">Transforma tu presencia digital</h1>
        <p class="text-xl mb-8">Soluciones web personalizadas para hacer crecer tu negocio en línea.</p>
        <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
          <NuxtLink 
            to="/contacto" 
            class="bg-white text-indigo-600 px-6 py-3 rounded-lg font-medium hover:bg-gray-100 transition-colors text-center"
          >
            Comenzar
          </NuxtLink>
          <NuxtLink 
            to="/servicios" 
            class="border-2 border-white px-6 py-3 rounded-lg font-medium hover:bg-white hover:text-indigo-600 transition-colors text-center"
          >
            Saber más
          </NuxtLink>
        </div>
      </div>
      
      <!-- Imagen/Ilustración -->
      <div class="md:w-1/2 flex justify-center">
        <img 
          src="/img/happy.png" 
          alt="Ilustración digital" 
          class="rounded-lg shadow-xl max-w-full h-auto"
          loading="lazy"
        >
      </div>
    </div>
  </section>
</template>