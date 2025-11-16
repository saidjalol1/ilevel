<template>
  <section class="relative bg-gradient-to-br from-gray-900 via-gray-800 to-black text-white overflow-hidden">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 lg:gap-8 items-center min-h-[500px] sm:min-h-[550px] lg:min-h-[600px] py-8 lg:py-0">
        <!-- Left Content -->
        <div class="space-y-4 sm:space-y-6 lg:space-y-8 z-10 order-2 lg:order-1">
          <p class="text-gray-400 text-sm sm:text-base font-light tracking-wide uppercase animate-fade-in-up">
           Ilevel
          </p>
          
          <h1 class="text-4xl sm:text-5xl lg:text-6xl xl:text-7xl font-light leading-tight animate-fade-in-up" style="animation-delay: 0.2s;">
            IPhone 14 <span class="font-bold">Pro</span>
          </h1>
          
          <p class="text-gray-300 text-base sm:text-lg lg:text-xl font-light max-w-md animate-fade-in-up" style="animation-delay: 0.4s;">
            Hamma narsani yaxshi tomonga o'zgartirish uchun yaratilgan. Hamma uchun
          </p>
          
          <div class="animate-fade-in-up" style="animation-delay: 0.6s;">
            <button 
              @click="handleShopNow"
              class="px-6 sm:px-8 py-3 cursor-pointer border-2 border-white text-white hover:bg-white hover:text-black transition-all duration-300 rounded font-medium text-sm sm:text-base transform hover:scale-105 active:scale-95"
            >
              Sotib oling
            </button>
          </div>
        </div>

        <!-- Right Content - Product Image -->
        <div class="relative h-full flex items-center justify-center lg:justify-end order-1 lg:order-2 mt-25">
          <div class="relative w-full max-w-[280px] sm:max-w-[350px] lg:max-w-[450px] xl:max-w-[500px] h-[300px] sm:h-[400px] lg:h-[500px]">
            <img 
              :src="productImage" 
              :alt="productAlt"
              class="w-full h-full object-contain drop-shadow-2xl animate-float"
            />
          </div>
        </div>
      </div>
    </div>

    <!-- Optional: Decorative gradient overlay -->
    <div class="absolute inset-0 bg-gradient-to-r from-purple-900/20 via-transparent to-blue-900/10 pointer-events-none"></div>
    
    <!-- Scroll indicator -->
    <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 animate-bounce">
      <div class="w-6 h-10 border-2 border-white rounded-full flex justify-center">
        <div class="w-1 h-3 bg-white rounded-full mt-2 animate-scroll"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

// Props to make the component reusable
const props = defineProps({
  tagline: {
    type: String,
    default: 'Pro.Beyond.'
  },
  title: {
    type: String,
    default: 'IPhone 14'
  },
  titleBold: {
    type: String,
    default: 'Pro'
  },
  description: {
    type: String,
    default: 'Created to change everything for the better. For everyone'
  },
  buttonText: {
    type: String,
    default: 'Shop Now'
  },
  productImage: {
    type: String,
    default: '20ae4cc7d95ed194279d337796d951679b146d4a.png' // Replace with your image path
  },
  productAlt: {
    type: String,
    default: 'iPhone 14 Pro'
  }
})

// Optional: Add click handler for button
const handleShopNow = () => {
  // Navigate to shop page or emit event
  console.log('Shop Now clicked')
}
</script>

<style scoped>
/* Smooth scroll behavior */
html {
  scroll-behavior: smooth;
}

/* Custom animations */
@keyframes fade-in-up {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes scroll {
  0% {
    transform: translateY(0);
    opacity: 1;
  }
  100% {
    transform: translateY(10px);
    opacity: 0;
  }
}

.animate-fade-in-up {
  animation: fade-in-up 0.8s ease-out forwards;
  opacity: 0;
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}

.animate-scroll {
  animation: scroll 2s infinite;
}

.drop-shadow-2xl {
  filter: drop-shadow(0 25px 50px rgba(0, 0, 0, 0.5));
}

/* Smooth transitions for all interactive elements */
* {
  transition-property: color, background-color, border-color, transform, opacity;
  transition-duration: 0.3s;
  transition-timing-function: ease-out;
}

/* Responsive improvements */
@media (max-width: 640px) {
  .animate-fade-in-up {
    animation-duration: 0.6s;
  }
  
  .animate-float {
    animation-duration: 4s;
  }
}

/* Enhanced hover effects */
button {
  position: relative;
  overflow: hidden;
}

button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
  transition: left 0.5s;
}

button:hover::before {
  left: 100%;
}

/* Smooth image loading */
img {
  transition: opacity 0.5s ease-in-out;
}

img:not([src]) {
  opacity: 0;
}

img[src] {
  opacity: 1;
}
</style>