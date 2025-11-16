<template>
  <div class="bg-gray-200">
    <!-- Footer -->
    <footer class="bg-black text-white py-16">
      <div class="max-w-7xl mx-auto px-4">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
          <!-- Company Info -->
          <div 
            :class="[
              'transition-all duration-1000',
              footerVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
            ]"
          >
            <h3 class="text-2xl font-bold mb-6">
                <NuxtImg 
                    src="logo.jpg" 
                    width="50" 
                    height="50"
                    class="transform hover:scale-105 transition-transform duration-300 cursor-pointer"
                />
            </h3>
            <p class="text-gray-400 mb-6 leading-relaxed">
              Biz Toshkentda joylashgan ichki dizayn bo'yicha yetakchi kompaniyamiz. 
              Bizning butik-studiyamiz an'anaviy usullardan ko'ra ko'proq imkoniyatlar taqdim etadi.
            </p>
            <div class="flex space-x-4">
              <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-gray-700 transition-all duration-300 transform hover:scale-110">
                <span class="text-xl">𝕏</span>
              </a>
              <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-gray-700 transition-all duration-300 transform hover:scale-110">
                <span class="text-xl">f</span>
              </a>
              <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-gray-700 transition-all duration-300 transform hover:scale-110">
                <span class="text-xl">♪</span>
              </a>
              <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-gray-700 transition-all duration-300 transform hover:scale-110">
                <span class="text-xl">📷</span>
              </a>
            </div>
          </div>

          <!-- Contact Info -->
          <div 
            :class="[
              'transition-all duration-1000 delay-200',
              footerVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
            ]"
          >
            <h3 class="text-xl font-bold mb-6">Aloqa ma'lumotlari</h3>
            <div class="space-y-4">
              <div class="group">
                <h4 class="text-gray-400 text-sm mb-1">Manzil</h4>
                <p class="text-white group-hover:text-blue-400 transition-colors duration-300">
                  Toshkent shahri, Yunusobod tumani, Amir Temur shox ko'chasi, 123-uy
                </p>
              </div>
              <div class="group">
                <h4 class="text-gray-400 text-sm mb-1">Telefon raqamlari</h4>
                <p class="text-white group-hover:text-blue-400 transition-colors duration-300">
                  +998 91 610 36 46
                </p>
                <p class="text-white group-hover:text-blue-400 transition-colors duration-300">
                  +998 50 222 69 79
                </p>
              </div>
              <div class="group">
                <h4 class="text-gray-400 text-sm mb-1">Elektron pochta</h4>
                <p class="text-white group-hover:text-blue-400 transition-colors duration-300">
                  saidjalolturakhujayev@gmail.com
                </p>
                <p class="text-white group-hover:text-blue-400 transition-colors duration-300">
                  saidjalolturakhujayev69@gmail.com
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)
const footerVisible = ref(false)
const heroRef = ref(null)

onMounted(() => {
  // Smooth entrance animation
  setTimeout(() => {
    isVisible.value = true
  }, 100)

  // Smooth scroll observer for footer
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          footerVisible.value = true
        }
      })
    },
    { threshold: 0.1 }
  )

  // Observe footer
  const footer = document.querySelector('footer')
  if (footer) {
    observer.observe(footer)
  }

  // Smooth scrolling for the entire page
  document.documentElement.style.scrollBehavior = 'smooth'
})
</script>

<style scoped>
/* Additional smooth scrolling styles */
* {
  scroll-behavior: smooth;
}
</style>