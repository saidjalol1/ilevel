<template>
  <div id="products-section" class="min-h-screen bg-gray-50 py-8 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <!-- Tabs Navigation -->
      <div class="flex gap-6 sm:gap-8 border-b border-gray-200 mb-8 overflow-x-auto scrollbar-hide">
        <button
          v-for="tab in tabs"
          :key="tab"
          @click="activeTab = tab"
          :class="[
            'pb-4 px-1 sm:px-2 whitespace-nowrap text-sm font-medium transition-all duration-300 relative',
            activeTab === tab
              ? 'text-black font-semibold'
              : 'text-gray-500 hover:text-gray-700'
          ]"
        >
          {{ tab }}
          <span 
            v-if="activeTab === tab"
            class="absolute bottom-0 left-0 w-full h-0.5 bg-black transform origin-left transition-all duration-300"
          ></span>
        </button>
      </div>

      <!-- Products Grid -->
      <div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-4 gap-3 sm:gap-6">
        <div
          v-for="(product, index) in products"
          :key="index"
          class="bg-white rounded-xl p-3 sm:p-6 shadow-sm hover:shadow-xl transition-all duration-500 transform hover:-translate-y-2 group"
        >
          <!-- Wishlist Icon -->
          <div class="flex justify-end mb-3">
            <button
              @click="toggleWishlist(index)"
              class="p-2 rounded-full hover:bg-red-50 transition-all duration-300 transform hover:scale-110"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                :class="[
                  'w-5 h-5 sm:w-6 sm:h-6 transition-all duration-300',
                  product.isWishlisted 
                    ? 'fill-red-500 stroke-red-500' 
                    : 'fill-white stroke-gray-400 group-hover:stroke-red-400'
                ]"
                stroke-width="1.5"
              >
                <path stroke-linecap="round" stroke-linejoin="round" d="M21 8.25c0-2.485-2.099-4.5-4.688-4.5-1.935 0-3.597 1.126-4.312 2.733-.715-1.607-2.377-2.733-4.313-2.733C5.1 3.75 3 5.765 3 8.25c0 7.22 9 12 9 12s9-4.78 9-12z" />
              </svg>
            </button>
          </div>

          <!-- Product Image -->
          <div class="flex justify-center items-center mb-4 h-28 sm:h-40 p-2">
            <img
              :src="product.image"
              :alt="product.name"
              class="max-h-full max-w-full object-contain transform group-hover:scale-105 transition-transform duration-500"
              loading="lazy"
            />
          </div>

          <!-- Product Info -->
          <div class="text-center space-y-3">
            <h3 class="text-xs sm:text-sm font-medium text-gray-900 line-clamp-2 min-h-[2.5rem] leading-tight">
              {{ product.name }}
            </h3>
            <p class="text-lg sm:text-xl font-bold text-gray-900">
              ${{ product.price }}
            </p>

            <!-- Buy Now Button -->
            <button
              class="w-full bg-black text-white py-2.5 sm:py-3 px-4 rounded-lg font-medium hover:bg-gray-800 transition-all duration-300 transform hover:scale-105 active:scale-95 text-sm sm:text-base group/btn"
            >
              <span class="flex items-center justify-center gap-2">
                Hozir sotib olish
                <svg class="w-4 h-4 transform group-hover/btn:translate-x-1 transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"/>
                </svg>
              </span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const tabs = ['Yangi Mahsulotlar', 'Eng Sotiladigan', 'Tavsiya Etilgan'];
const activeTab = ref('Yangi Mahsulotlar');

const products = ref([
  {
    name: 'Apple iPhone 14 Pro Max 128GB Deep Purple',
    price: 900,
    image: 'iphone14.png',
    isWishlisted: false
  },
  {
    name: 'Blackmagic Pocket Cinema Camera 6K',
    price: 2535,
    image: 'camera.png',
    isWishlisted: false
  },
  {
    name: 'Apple Watch Series 9 GPS 41mm Starlight Aluminium',
    price: 399,
    image: 'applewatch.png',
    isWishlisted: false
  },
  {
    name: 'AirPods Max Silver Starlight Aluminium',
    price: 549,
    image: 'headphone.png',
    isWishlisted: false
  },
  {
    name: 'Samsung Galaxy Watch6 Classic 47mm Black',
    price: 369,
    image: 'watch.png',
    isWishlisted: false
  },
  {
    name: 'Galaxy Z Fold5 Unlocked | 256GB | Phantom Black',
    price: 1799,
    image: 'galaxyz.png',
    isWishlisted: true
  },
  {
    name: 'Galaxy Buds FE Graphite',
    price: 99.99,
    image: 'earbuds.png',
    isWishlisted: false
  },
  {
    name: 'Apple iPad 9 10.2" 64GB Wi-Fi Silver',
    price: 398,
    image: 'ipad.png',
    isWishlisted: false
  }
]);

const toggleWishlist = (index) => {
  products.value[index].isWishlisted = !products.value[index].isWishlisted;
};

// Smooth scroll animation when section comes into view
const setupIntersectionObserver = () => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('animate-fade-in-up');
          // Animate products with staggered delay
          const products = entry.target.querySelectorAll('.product-card');
          products.forEach((product, index) => {
            product.style.animationDelay = `${index * 0.1}s`;
          });
        }
      });
    },
    {
      threshold: 0.1,
      rootMargin: '0px 0px -50px 0px'
    }
  );

  const section = document.getElementById('products-section');
  if (section) {
    observer.observe(section);
  }
};

onMounted(() => {
  setupIntersectionObserver();
});
</script>

<style scoped>
/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Hide scrollbar for tab navigation */
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}

.scrollbar-hide {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

/* Line clamp for product names */
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* Smooth fade-in animation */
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

.animate-fade-in-up {
  animation: fade-in-up 0.6s ease-out forwards;
  opacity: 0;
}

/* Enhanced hover effects */
.product-card {
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Smooth transitions for all interactive elements */
* {
  transition-property: color, background-color, border-color, transform, opacity;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Custom scroll behavior for smooth animations */
@media (prefers-reduced-motion: no-preference) {
  .smooth-scroll {
    scroll-behavior: smooth;
  }
}

/* Enhanced focus states for accessibility */
button:focus-visible {
  outline: 2px solid #3b82f6;
  outline-offset: 2px;
}

/* Mobile optimizations */
@media (max-width: 640px) {
  .product-card {
    border-radius: 12px;
  }
  
  .animate-fade-in-up {
    animation-duration: 0.4s;
  }
}

/* Professional shadow effects */
.shadow-sm {
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
}

.hover\:shadow-xl:hover {
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
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

/* Enhanced button hover effects */
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
</style>