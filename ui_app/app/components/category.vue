<template>
  <div id="categories-section" class="w-full py-12 px-4 md:px-6 lg:px-8 bg-white">
    <div class="max-w-7xl mx-auto">
      <!-- Header -->
      <div class="flex items-center justify-between mb-8">
        <h2 class="text-2xl md:text-3xl font-semibold text-gray-900">
          Bo'limlar
        </h2>
        
        <!-- Navigation Arrows - Desktop -->
        <div class="hidden md:flex items-center gap-2">
          <button
            @click="scroll('left')"
            :disabled="!showLeftArrow"
            :class="[
              'w-10 h-10 rounded-full flex items-center justify-center transition-all duration-300',
              showLeftArrow
                ? 'bg-gray-100 hover:bg-gray-200 text-gray-800 cursor-pointer'
                : 'bg-gray-50 text-gray-300 cursor-not-allowed'
            ]"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 16 16">
              <path fill-rule="evenodd" d="M11.354 1.646a.5.5 0 0 1 0 .708L5.707 8l5.647 5.646a.5.5 0 0 1-.708.708l-6-6a.5.5 0 0 1 0-.708l6-6a.5.5 0 0 1 .708 0z"/>
            </svg>
          </button>
          <button
            @click="scroll('right')"
            :disabled="!showRightArrow"
            :class="[
              'w-10 h-10 rounded-full flex items-center justify-center transition-all duration-300',
              showRightArrow
                ? 'bg-gray-100 hover:bg-gray-200 text-gray-800 cursor-pointer'
                : 'bg-gray-50 text-gray-300 cursor-not-allowed'
            ]"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 16 16">
              <path fill-rule="evenodd" d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z"/>
            </svg>
          </button>
        </div>
      </div>

      <!-- Categories Scroll Container -->
      <div class="relative">
        <div
          ref="scrollContainer"
          @scroll="checkScrollPosition"
          class="flex gap-4 overflow-x-auto scroll-smooth scrollbar-hide pb-4 "
        >
          <div
            v-for="category in categories"
            :key="category.id"
            class="category-card flex-shrink-0 w-32 sm:w-36 md:w-40 lg:w-44 "
          >
            <button
              class="w-full cursor-pointer h-full flex flex-col items-center justify-center gap-3 p-6 bg-gray-50 hover:bg-gray-100 rounded-xl transition-all duration-300 hover:shadow-md group"
            >
              <div class="w-12 h-12 md:w-14 md:h-14 flex items-center justify-center text-gray-700 group-hover:text-gray-900 transition-colors duration-300">
                <p v-html="category.icon"></p>
              </div>
              <span class="text-sm md:text-base font-medium text-gray-800 text-center">
                {{ category.name }}
              </span>
            </button>
          </div>
        </div>

        <!-- Mobile Navigation Arrows -->
        <div class="flex md:hidden items-center justify-center gap-3 mt-4">
          <button
            @click="scroll('left')"
            :disabled="!showLeftArrow"
            :class="[
              'w-9 h-9 rounded-full flex items-center justify-center transition-all duration-300',
              showLeftArrow
                ? 'bg-gray-100 text-gray-800 cursor-pointer'
                : 'bg-gray-50 text-gray-300 cursor-not-allowed'
            ]"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 16 16">
              <path fill-rule="evenodd" d="M11.354 1.646a.5.5 0 0 1 0 .708L5.707 8l5.647 5.646a.5.5 0 0 1-.708.708l-6-6a.5.5 0 0 1 0-.708l6-6a.5.5 0 0 1 .708 0z"/>
            </svg>
          </button>
          <button
            @click="scroll('right')"
            :disabled="!showRightArrow"
            :class="[
              'w-9 h-9 rounded-full flex items-center justify-center transition-all duration-300',
              showRightArrow
                ? 'bg-gray-100 text-gray-800 cursor-pointer'
                : 'bg-gray-50 text-gray-300 cursor-not-allowed'
            ]"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 16 16">
              <path fill-rule="evenodd" d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z"/>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const scrollContainer = ref<HTMLElement | null>(null)
const showLeftArrow = ref(false)
const showRightArrow = ref(true)

// Define all icon components
const PhoneIcon = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="currentColor" viewBox="0 0 16 16">
      <path d="M11 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h6zM5 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2H5z"/>
      <path d="M8 14a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"/>
    </svg>
  `
}

const WatchIcon = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="currentColor" viewBox="0 0 16 16">
      <path d="M8.5 5a.5.5 0 0 0-1 0v2.5H6a.5.5 0 0 0 0 1h2a.5.5 0 0 0 .5-.5V5z"/>
      <path d="M6.5 1A.5.5 0 0 1 7 .5h2a.5.5 0 0 1 0 1v.57c1.36.196 2.594.78 3.584 1.64a.715.715 0 0 1 .012-.013l.354-.354-.354-.353a.5.5 0 0 1 .707-.708l1.414 1.415a.5.5 0 1 1-.707.707l-.353-.354-.354.354a.512.512 0 0 1-.013.012A7 7 0 1 1 7 2.071V1.5a.5.5 0 0 1-.5-.5zM8 3a6 6 0 1 0 .001 12A6 6 0 0 0 8 3z"/>
    </svg>
  `
}

const CameraIcon = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="currentColor" viewBox="0 0 16 16">
      <path d="M15 12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V6a1 1 0 0 1 1-1h1.172a3 3 0 0 0 2.12-.879l.83-.828A1 1 0 0 1 6.827 3h2.344a1 1 0 0 1 .707.293l.828.828A3 3 0 0 0 12.828 5H14a1 1 0 0 1 1 1v6zM2 4a2 2 0 0 0-2 2v6a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2h-1.172a2 2 0 0 1-1.414-.586l-.828-.828A2 2 0 0 0 9.172 2H6.828a2 2 0 0 0-1.414.586l-.828.828A2 2 0 0 1 3.172 4H2z"/>
      <path d="M8 11a2.5 2.5 0 1 1 0-5 2.5 2.5 0 0 1 0 5zm0 1a3.5 3.5 0 1 0 0-7 3.5 3.5 0 0 0 0 7zM3 6.5a.5.5 0 1 1-1 0 .5.5 0 0 1 1 0z"/>
    </svg>
  `
}

const HeadphonesIcon = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="currentColor" viewBox="0 0 16 16">
      <path d="M8 3a5 5 0 0 0-5 5v1h1a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V8a6 6 0 1 1 12 0v5a1 1 0 0 1-1 1h-1a1 1 0 0 1-1-1v-3a1 1 0 0 1 1-1h1V8a5 5 0 0 0-5-5z"/>
    </svg>
  `
}

const ComputerIcon = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="currentColor" viewBox="0 0 16 16">
      <path d="M2 2a2 2 0 0 0-2 2v7a2 2 0 0 0 2 2h11a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2H2zm11 1a1 1 0 0 1 1 1v7a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V4a1 1 0 0 1 1-1h11zM2 14a1 1 0 0 0-1 1v1h14v-1a1 1 0 0 0-1-1H2z"/>
    </svg>
  `
}

const GamingIcon = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="currentColor" viewBox="0 0 16 16">
      <path d="M11.5 6.027a.5.5 0 1 1-1 0 .5.5 0 0 1 1 0zm-1.5 1.5a.5.5 0 1 0 0-1 .5.5 0 0 0 0 1zm2.5-.5a.5.5 0 1 1-1 0 .5.5 0 0 1 1 0zm-1.5 1.5a.5.5 0 1 0 0-1 .5.5 0 0 0 0 1zm-6.5-3h1v1h1v1h-1v1h-1v-1h-1v-1h1v-1z"/>
      <path d="M3.051 3.26a.5.5 0 0 1 .354-.613l1.932-.518a.5.5 0 0 1 .62.39c.655-.079 1.35-.117 2.043-.117.72 0 1.443.041 2.12.126a.5.5 0 0 1 .622-.399l1.932.518a.5.5 0 0 1 .306.729c.14.09.266.19.373.297.408.408.78 1.05 1.095 1.772.32.733.599 1.591.805 2.466.206.875.34 1.78.364 2.606.024.816-.059 1.602-.328 2.21a1.42 1.42 0 0 1-1.445.83c-.636-.067-1.115-.394-1.513-.773-.245-.232-.496-.526-.739-.808-.126-.148-.25-.292-.368-.423-.728-.804-1.597-1.527-3.224-1.527-1.627 0-2.496.723-3.224 1.527-.119.131-.242.275-.368.423-.243.282-.494.575-.739.808-.398.38-.877.706-1.513.773a1.42 1.42 0 0 1-1.445-.83c-.27-.608-.352-1.395-.329-2.21.024-.826.16-1.73.365-2.606.206-.875.486-1.733.805-2.466.315-.722.687-1.364 1.094-1.772a2.34 2.34 0 0 1 .433-.335.504.504 0 0 1-.028-.079zm2.036.412c-.877.185-1.469.443-1.733.708-.276.276-.587.783-.885 1.465a13.748 13.748 0 0 0-.748 2.295 12.351 12.351 0 0 0-.339 2.406c-.022.755.062 1.368.243 1.776a.42.42 0 0 0 .426.24c.327-.034.61-.199.929-.502.212-.202.4-.423.615-.674.133-.156.27-.323.415-.504C4.861 9.969 5.978 9.027 8 9.027s3.139.942 3.965 1.855c.145.181.282.348.415.504.214.251.403.472.615.674.318.303.601.468.929.503a.42.42 0 0 0 .426-.241c.18-.408.265-1.02.243-1.776a12.354 12.354 0 0 0-.339-2.406 13.753 13.753 0 0 0-.748-2.295c-.298-.682-.61-1.19-.885-1.465-.264-.265-.856-.523-1.733-.708-.85-.179-1.877-.27-2.913-.27-1.036 0-2.063.091-2.913.27z"/>
    </svg>
  `
}


const categories = [
  {
    id: 1,
    name: 'Telefonlar',
    icon: PhoneIcon.template
  },
  {
    id: 2,
    name: 'Smart Watchelar',
    icon: WatchIcon.template
  },
  {
    id: 3,
    name: 'Kameralar',
    icon: CameraIcon.template
  },
  {
    id: 4,
    name: 'Quloqchinlar',
    icon: HeadphonesIcon.template
  },
  {
    id: 5,
    name: 'Kompyuterlar',
    icon: ComputerIcon.template
  },
  {
    id: 6,
    name: 'Gaming',
    icon: GamingIcon.template
  }
]



const checkScrollPosition = () => {
  const container = scrollContainer.value
  if (!container) return

  showLeftArrow.value = container.scrollLeft > 0
  showRightArrow.value = 
    container.scrollLeft < container.scrollWidth - container.clientWidth - 10
}

const scroll = (direction: 'left' | 'right') => {
  const container = scrollContainer.value
  if (!container) return

  const scrollAmount = 300
  const targetScroll = direction === 'left' 
    ? container.scrollLeft - scrollAmount 
    : container.scrollLeft + scrollAmount

  container.scrollTo({
    left: targetScroll,
    behavior: 'smooth'
  })
}

// Smooth scroll when section comes into view
const setupIntersectionObserver = () => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('animate-fade-in-up')
        }
      })
    },
    {
      threshold: 0.1,
      rootMargin: '0px 0px -50px 0px'
    }
  )

  const section = document.getElementById('categories-section')
  if (section) {
    observer.observe(section)
  }
}

onMounted(() => {
  checkScrollPosition()
  window.addEventListener('resize', checkScrollPosition)
  setupIntersectionObserver()
})

onUnmounted(() => {
  window.removeEventListener('resize', checkScrollPosition)
})
</script>

<style scoped>
.scrollbar-hide {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.scrollbar-hide::-webkit-scrollbar {
  display: none;
}

.category-card {
  scroll-snap-align: start;
}

* {
  scroll-behavior: smooth;
}

/* Smooth scroll animation when section comes into view */
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
}

/* Smooth transitions for all interactive elements */
.category-card {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.category-card:hover {
  transform: translateY(-4px);
}

/* Smooth scrolling for the entire page */
html {
  scroll-behavior: smooth;
}

/* Enhanced button hover effects */
button:not(:disabled):hover {
  transform: scale(1.05);
}

/* Smooth icon transitions */
svg {
  transition: all 0.3s ease;
}
</style>