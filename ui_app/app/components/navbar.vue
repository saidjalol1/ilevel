<template>
  <nav class="bg-white shadow-sm sticky top-0 z-50 transition-all duration-300">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center gap-4 h-16">
        <!-- Logo and Search -->
        <div class="flex items-center flex-1">
          <NuxtImg 
            src="logo.jpg" 
            width="50" 
            height="50"
            class="transform hover:scale-105 transition-transform duration-300 cursor-pointer"
          />
          
          <!-- Desktop Search -->
          <div class="hidden md:block ml-8 flex-1 max-w-md">
            <div class="relative">
              <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="text-gray-400 transition-colors duration-300" viewBox="0 0 16 16">
                  <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
                </svg>
              </div>
              <input
                type="text"
                placeholder="Qidiruv"
                class="block w-full pl-10 pr-3 py-2 border border-gray-300 rounded-lg bg-gray-50 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm transition-all duration-300 hover:border-gray-400"
              />
            </div>
          </div>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center space-x-8">
          <NuxtLink 
            to="/" 
            class="text-gray-900 hover:text-black-600 font-medium transition-all duration-300 transform hover:scale-105 relative group"
          >
            Asosiy
            <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-black transition-all duration-300 group-hover:w-full"></span>
          </NuxtLink>
          <NuxtLink 
            to="/market" 
            class="text-gray-400 hover:text-black-600 font-medium transition-all duration-300 transform hover:scale-105 relative group"
          >
            Do'kon
            <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-black transition-all duration-300 group-hover:w-full"></span>
          </NuxtLink>
          <NuxtLink 
            to="/contact" 
            class="text-gray-400 hover:text-black-600 font-medium transition-all duration-300 transform hover:scale-105 relative group"
          >
            Bog'lanish
            <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-black transition-all duration-300 group-hover:w-full"></span>
          </NuxtLink>
          
          <!-- Icons -->
          <NuxtLink 
            to="/favorites" 
            class="text-gray-900 hover:text-red-500 transition-all duration-300 transform hover:scale-110 relative group"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 16 16">
              <path d="m8 2.748-.717-.737C5.6.281 2.514.878 1.4 3.053c-.523 1.023-.641 2.5.314 4.385.92 1.815 2.834 3.989 6.286 6.357 3.452-2.368 5.365-4.542 6.286-6.357.955-1.886.838-3.362.314-4.385C13.486.878 10.4.28 8.717 2.01L8 2.748zM8 15C-7.333 4.868 3.279-3.04 7.824 1.143c.06.055.119.112.176.171a3.12 3.12 0 0 1 .176-.17C12.72-3.042 23.333 4.867 8 15z"/>
            </svg>
            <span class="absolute -top-2 -right-2 bg-red-500 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              3
            </span>
          </NuxtLink>
          <NuxtLink 
            to="/cart" 
            class="text-gray-900 hover:text-green-600 transition-all duration-300 transform hover:scale-110 relative group"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 16 16">
              <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM3.102 4l1.313 7h8.17l1.313-7H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
            </svg>
            <span class="absolute -top-2 -right-2 bg-green-600 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              2
            </span>
          </NuxtLink>
        </div>

        <!-- Mobile menu button -->
        <button
          @click="toggleMobileMenu"
          class="md:hidden inline-flex items-center justify-center p-2 rounded-md text-gray-900 hover:text-blue-600 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-blue-500 transition-all duration-300 transform hover:scale-110"
        >
          <svg v-if="!mobileMenuOpen" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 16 16" class="transition-transform duration-300">
            <path fill-rule="evenodd" d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"/>
          </svg>
          <svg v-else xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 16 16" class="transition-transform duration-300">
            <path d="M2.146 2.854a.5.5 0 1 1 .708-.708L8 7.293l5.146-5.147a.5.5 0 0 1 .708.708L8.707 8l5.147 5.146a.5.5 0 0 1-.708.708L8 8.707l-5.146 5.147a.5.5 0 0 1-.708-.708L7.293 8 2.146 2.854Z"/>
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile menu -->
    <div 
      v-if="mobileMenuOpen" 
      class="md:hidden border-t border-gray-200 transition-all duration-500 ease-in-out"
      :class="mobileMenuOpen ? 'max-h-96 opacity-100' : 'max-h-0 opacity-0'"
    >
      <div class="px-4 pt-2 pb-3 space-y-1">
        <!-- Mobile Search -->
        <div class="relative mb-3 animate-fade-in">
          <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="text-gray-400" viewBox="0 0 16 16">
              <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
            </svg>
          </div>
          <input
            type="text"
            placeholder="Qidiruv"
            class="block w-full pl-10 pr-3 py-2 border border-gray-300 rounded-lg bg-gray-50 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm transition-all duration-300"
          />
        </div>

        <!-- Mobile Navigation Links -->
        <NuxtLink
          to="/"
          @click="closeMobileMenu"
          class="block px-3 py-3 rounded-md text-base font-medium text-gray-900 hover:bg-blue-50 hover:text-blue-600 transition-all duration-300 transform hover:translate-x-2 border-l-4 border-transparent hover:border-blue-600"
        >
          Asosiy
        </NuxtLink>
        <NuxtLink
          to="/about"
          @click="closeMobileMenu"
          class="block px-3 py-3 rounded-md text-base font-medium text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all duration-300 transform hover:translate-x-2 border-l-4 border-transparent hover:border-blue-600"
        >
          Do'kon
        </NuxtLink>
        <NuxtLink
          to="/contact"
          @click="closeMobileMenu"
          class="block px-3 py-3 rounded-md text-base font-medium text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all duration-300 transform hover:translate-x-2 border-l-4 border-transparent hover:border-blue-600"
        >
          Bog'lanish
        </NuxtLink>

        <!-- Mobile Icons -->
        <div class="flex items-center justify-around px-3 py-4 border-t border-gray-200 mt-3 animate-fade-in-delayed">
          <NuxtLink 
            to="/favorites" 
            @click="closeMobileMenu"
            class="text-gray-900 hover:text-red-500 transition-all duration-300 transform hover:scale-110 flex flex-col items-center group"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 16 16">
              <path d="m8 2.748-.717-.737C5.6.281 2.514.878 1.4 3.053c-.523 1.023-.641 2.5.314 4.385.92 1.815 2.834 3.989 6.286 6.357 3.452-2.368 5.365-4.542 6.286-6.357.955-1.886.838-3.362.314-4.385C13.486.878 10.4.28 8.717 2.01L8 2.748zM8 15C-7.333 4.868 3.279-3.04 7.824 1.143c.06.055.119.112.176.171a3.12 3.12 0 0 1 .176-.17C12.72-3.042 23.333 4.867 8 15z"/>
            </svg>
            <span class="text-xs mt-1 text-gray-600 group-hover:text-red-500">Sevimlilar</span>
            <span class="absolute top-0 right-0 bg-red-500 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center transform translate-x-1 -translate-y-1">
              3
            </span>
          </NuxtLink>
          <NuxtLink 
            to="/cart" 
            @click="closeMobileMenu"
            class="text-gray-900 hover:text-green-600 transition-all duration-300 transform hover:scale-110 flex flex-col items-center group relative"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 16 16">
              <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM3.102 4l1.313 7h8.17l1.313-7H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
            </svg>
            <span class="text-xs mt-1 text-gray-600 group-hover:text-green-600">Savat</span>
            <span class="absolute top-0 right-0 bg-green-600 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center transform translate-x-1 -translate-y-1">
              2
            </span>
          </NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}

// Close mobile menu when clicking outside
const handleClickOutside = (event) => {
  const nav = document.querySelector('nav')
  if (nav && !nav.contains(event.target)) {
    mobileMenuOpen.value = false
  }
}

onMounted(() => {
  document.addEventListener('click', handleClickOutside)
})

onUnmounted(() => {
  document.removeEventListener('click', handleClickOutside)
})
</script>

<style scoped>
/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Custom animations */
@keyframes fade-in {
  0% {
    opacity: 0;
    transform: translateY(-10px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fade-in-delayed {
  0% {
    opacity: 0;
    transform: translateY(-10px);
  }
  50% {
    opacity: 0;
    transform: translateY(-10px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fade-in 0.5s ease-out forwards;
}

.animate-fade-in-delayed {
  animation: fade-in-delayed 0.8s ease-out forwards;
}

/* Smooth transitions for all interactive elements */
* {
  transition-property: color, background-color, border-color, transform, opacity, max-height;
  transition-duration: 0.3s;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Sticky nav shadow effect */
nav {
  backdrop-filter: blur(10px);
}

/* Active link styles */
.router-link-active {
  color: black;
}

.router-link-active span {
  width: 100%;
}

/* Mobile menu backdrop */
@media (max-width: 768px) {
  nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    width: 100%;
  }
  
  body {
    padding-top: 64px; /* Adjust based on nav height */
  }
}

/* Enhanced focus styles for accessibility */
button:focus-visible,
input:focus-visible,
a:focus-visible {
  outline: 2px solid black;
  outline-offset: 2px;
}

/* Smooth hover effects for touch devices */
@media (hover: hover) {
  .hover-scale:hover {
    transform: scale(1.05);
  }
}
</style>