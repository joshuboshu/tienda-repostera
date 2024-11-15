<script setup>
import { ref } from 'vue'

const cartCount = ref(0)
const isMenuOpen = ref(false)
</script>

<template>
  <nav class="bg-white/80 backdrop-blur-md shadow-lg fixed w-full top-0 z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-16">
        <div class="flex items-center">
          <span class="text-2xl font-bold text-pink-600 hover:text-pink-700 transition-colors duration-300 cursor-pointer flex items-center gap-2">
            <span class="transform hover:scale-110 transition-transform duration-300 inline-block">🍰</span>
            <span class="hidden sm:inline">Dulces Delicias</span>
          </span>
        </div>
        
        <div class="hidden md:flex items-center space-x-8">
          <a href="#" class="text-gray-600 hover:text-pink-600 transition-colors duration-300">Inicio</a>
          <a href="#" class="text-gray-600 hover:text-pink-600 transition-colors duration-300">Menú</a>
          <a href="#" class="text-gray-600 hover:text-pink-600 transition-colors duration-300">Sobre Nosotros</a>
          <button class="relative p-2 group">
            <div class="absolute -inset-1 bg-gradient-to-r from-pink-600 to-purple-600 rounded-lg blur opacity-0 group-hover:opacity-25 transition duration-300"></div>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-600 group-hover:text-pink-600 transition-colors duration-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
            </svg>
            <span class="absolute -top-1 -right-1 bg-gradient-to-r from-pink-600 to-purple-600 text-white rounded-full w-5 h-5 flex items-center justify-center text-xs animate-pulse">
              {{ cartCount }}
            </span>
          </button>
        </div>

        <!-- Mobile menu button -->
        <div class="flex items-center md:hidden">
          <button @click="isMenuOpen = !isMenuOpen" class="p-2 rounded-md text-gray-600 hover:text-pink-600 focus:outline-none">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile menu -->
    <div v-show="isMenuOpen" class="md:hidden bg-white/80 backdrop-blur-md">
      <div class="px-2 pt-2 pb-3 space-y-1">
        <a href="#" class="block px-3 py-2 rounded-md text-gray-600 hover:text-pink-600 hover:bg-pink-50 transition-colors duration-300">Inicio</a>
        <a href="#" class="block px-3 py-2 rounded-md text-gray-600 hover:text-pink-600 hover:bg-pink-50 transition-colors duration-300">Menú</a>
        <a href="#" class="block px-3 py-2 rounded-md text-gray-600 hover:text-pink-600 hover:bg-pink-50 transition-colors duration-300">Sobre Nosotros</a>
      </div>
    </div>
  </nav>
</template>