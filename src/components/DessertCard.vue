<script setup>
import { ref } from 'vue'

const props = defineProps({
  title: String,
  price: Number,
  description: String,
  image: String,
  ingredients: Array,
  calories: Number
})

const showDetails = ref(false)
const isHovered = ref(false)
</script>

<template>
  <div 
    class="group bg-white rounded-xl shadow-lg overflow-hidden transform transition-all duration-500 hover:scale-[1.02] hover:shadow-xl relative"
    @mouseenter="isHovered = true"
    @mouseleave="isHovered = false"
  >
    <div class="relative overflow-hidden">
      <img 
        :src="image" 
        :alt="title" 
        class="w-full h-48 object-cover transition-transform duration-700 group-hover:scale-110"
      >
      <div class="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
      <div 
        class="absolute top-0 right-0 bg-gradient-to-l from-pink-600 to-purple-600 text-white px-4 py-2 rounded-bl-xl transform transition-transform duration-300"
        :class="{ 'translate-x-0': isHovered, 'translate-x-full': !isHovered }"
      >
        ${{ price.toFixed(2) }}
      </div>
    </div>
    <div class="p-6">
      <h3 class="text-xl font-bold text-gray-800 mb-2 group-hover:text-pink-600 transition-colors duration-300">{{ title }}</h3>
      <p class="text-gray-600 mb-4">{{ description }}</p>
      
      <div class="mb-4">
        <button 
          @click="showDetails = !showDetails"
          class="text-sm text-pink-600 hover:text-pink-700 flex items-center group/btn"
        >
          <span class="relative">
            {{ showDetails ? 'Ocultar detalles' : 'Ver detalles' }}
            <span class="absolute -bottom-1 left-0 w-full h-0.5 bg-pink-600 transform scale-x-0 group-hover/btn:scale-x-100 transition-transform duration-300"></span>
          </span>
          <svg 
            xmlns="http://www.w3.org/2000/svg" 
            class="h-4 w-4 ml-1 transform transition-transform duration-300"
            :class="{ 'rotate-180': showDetails }"
            fill="none" 
            viewBox="0 0 24 24" 
            stroke="currentColor"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
          </svg>
        </button>
      </div>

      <div 
        v-if="showDetails" 
        class="mb-4 space-y-2 transform transition-all duration-300"
        :class="{ 'opacity-100 translate-y-0': showDetails, 'opacity-0 -translate-y-4': !showDetails }"
      >
        <div class="text-sm text-gray-600">
          <strong>Calorías:</strong> {{ calories }} kcal
        </div>
        <div class="text-sm text-gray-600">
          <strong>Ingredientes:</strong>
          <ul class="list-disc list-inside ml-2">
            <li 
              v-for="ingredient in ingredients" 
              :key="ingredient"
              class="transform hover:translate-x-2 transition-transform duration-300"
            >
              {{ ingredient }}
            </li>
          </ul>
        </div>
      </div>

      <div class="flex space-x-2">
        <button class="group/cart flex-1 relative px-4 py-2 rounded-lg overflow-hidden">
          <div class="absolute inset-0 bg-gradient-to-r from-pink-600 to-purple-600 transition-transform duration-500 group-hover/cart:scale-105"></div>
          <div class="relative flex items-center justify-center text-white space-x-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 transform group-hover/cart:scale-110 transition-transform duration-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
            </svg>
            <span class="transform group-hover/cart:scale-105 transition-transform duration-300">Añadir al carrito</span>
          </div>
        </button>
      </div>
    </div>
  </div>
</template>