<template>
  <!-- Header/Navbar -->
  <header class="bg-white shadow-md sticky top-0 z-50">
    <div class="container mx-auto px-4 py-3 flex justify-between items-center">
      <!-- Logo con NuxtLink -->
      <NuxtLink to="/" class="flex items-center">
        <span class="text-2xl font-bold text-indigo-600">DigitalExp</span>
      </NuxtLink>
      
      <!-- Menú de navegación con NuxtLink -->
      <nav class="hidden md:flex space-x-8">
        <NuxtLink 
          to="/" 
          class="text-gray-600 hover:text-indigo-600 transition-colors"
          active-class="text-indigo-600 font-semibold"
        >
          Inicio
        </NuxtLink>
        <NuxtLink 
          to="/servicios" 
          class="text-gray-600 hover:text-indigo-600 transition-colors"
          active-class="text-indigo-600 font-semibold"
        >
          Servicios
        </NuxtLink>
        <NuxtLink 
          to="/nosotros" 
          class="text-gray-600 hover:text-indigo-600 transition-colors"
          active-class="text-indigo-600 font-semibold"
        >
          Nosotros
        </NuxtLink>
        <NuxtLink 
          to="/contacto" 
          class="text-gray-600 hover:text-indigo-600 transition-colors"
          active-class="text-indigo-600 font-semibold"
        >
          Contacto
        </NuxtLink>
      </nav>
      
      <!-- Botón móvil (hamburguesa) -->
      <button 
        class="md:hidden text-gray-600 focus:outline-none"
        @click="toggleMenu"
      >
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
        </svg>
      </button>
    </div>

    <!-- Menú móvil (aparece al hacer click) -->
    <div 
      v-if="isMenuOpen" 
      class="md:hidden bg-white py-4 px-4 shadow-lg"
    >
      <NuxtLink 
        to="/" 
        class="block py-2 text-gray-600 hover:text-indigo-600 transition-colors"
        active-class="text-indigo-600 font-semibold"
        @click="closeMenu"
      >
        Inicio
      </NuxtLink>
      <NuxtLink 
        to="/servicios" 
        class="block py-2 text-gray-600 hover:text-indigo-600 transition-colors"
        active-class="text-indigo-600 font-semibold"
        @click="closeMenu"
      >
        Servicios
      </NuxtLink>
      <NuxtLink 
        to="/nosotros" 
        class="block py-2 text-gray-600 hover:text-indigo-600 transition-colors"
        active-class="text-indigo-600 font-semibold"
        @click="closeMenu"
      >
        Nosotros
      </NuxtLink>
      <NuxtLink 
        to="/contacto" 
        class="block py-2 text-gray-600 hover:text-indigo-600 transition-colors"
        active-class="text-indigo-600 font-semibold"
        @click="closeMenu"
      >
        Contacto
      </NuxtLink>
    </div>
  </header>
</template>

<script setup>
// Composición con Composition API
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>