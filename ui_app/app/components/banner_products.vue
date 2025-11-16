<template>
  <div class="product-showcase">
    <div class="showcase-grid">
      <!-- PlayStation 5 -->
      <div class="product-card large">
        <div class="card-inner">
          <div class="product-image">
            <NuxtImg 
              src="ps5.png" 
              alt="PlayStation 5"
              loading="lazy"
            />
          </div>
          <div class="product-content">
            <h2 class="product-title">Playstation 5</h2>
            <p class="product-description">
              Nihoyatda kuchli protsessorlar, grafik protsessorlar va o'rnatilgan kirish/chiqishga ega SSD sizning PlayStation tajribangizni qayta belgilaydi.
            </p>
          </div>
        </div>
      </div>

      <!-- Apple AirPods Max -->
      <div class="product-card medium">
        <div class="card-inner">
          <div class="product-image">
            <NuxtImg  
              src="headphone.png" 
              alt="Apple AirPods Max"
              loading="lazy" 
            />
          </div>
          <div class="product-content">
            <h2 class="product-title">
              Apple<br />AirPods<br /><strong>Max</strong>
            </h2>
            <p class="product-description">
              Hisoblash audiosi. Eshiting, u juda kuchli
            </p>
          </div>
        </div>
      </div>

      <!-- Apple Vision Pro -->
      <div class="product-card medium dark">
        <div class="card-inner">
          <div class="product-image">
            <NuxtImg 
              src="apple_vision.png" 
              alt="Apple Vision Pro"
              loading="lazy"
            />
          </div>
          <div class="product-content">
            <h2 class="product-title">
              Apple<br />Vision <strong>Pro</strong>
            </h2>
            <p class="product-description">
              Ko'ngilochar tajribani his etishning ajoyib usuli
            </p>
          </div>
        </div>
      </div>

      <!-- MacBook Air -->
      <div class="product-card large">
        <div class="card-inner">
          <div class="product-image">
            <NuxtImg 
              src="pngimg.com - macbook_PNG9.png" 
              alt="MacBook Air"
              loading="lazy"
            />
          </div>
          <div class="product-content">
            <h2 class="product-title">
              Macbook<br /><strong>Air</strong>
            </h2>
            <p class="product-description">
              Yangi 15 dyuymli MacBook Air keng Liquid Retina displeyi bilan sizga yoqadigan narsalar uchun ko'proq joy ajratadi.
            </p>
            <button class="shop-button">Shop Now</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const cards = ref<HTMLElement[]>([])

const observerCallback = (entries: IntersectionObserverEntry[]) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible')
    }
  })
}

let observer: IntersectionObserver | null = null

onMounted(() => {
  observer = new IntersectionObserver(observerCallback, {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
  })

  const cardElements = document.querySelectorAll('.product-card')
  cardElements.forEach((card, index) => {
    ;(card as HTMLElement).style.transitionDelay = `${index * 0.1}s`
    observer?.observe(card)
  })
})

onUnmounted(() => {
  observer?.disconnect()
})
</script>

<style scoped>
* {
  scroll-behavior: smooth;
}

.product-showcase {
  width: 100%;
  padding: 2rem 1rem;
  background: linear-gradient(to bottom, #f5f5f7 0%, #e8e8ed 100%);
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.25rem;
  max-width: 1300px;
  margin: 0 auto;
}

.product-card {
  background: white;
  border-radius: 1.25rem;
  overflow: hidden;
  box-shadow: 0 2px 16px rgba(0, 0, 0, 0.06);
  transition: transform 0.3s ease, box-shadow 0.3s ease, opacity 0.6s ease, translate 0.6s ease;
  position: relative;
  opacity: 0;
  translate: 0 30px;
  cursor: pointer;
}

.product-card.visible {
  opacity: 1;
  translate: 0 0;
}

.product-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0, 0, 0, 0.12);
}

.product-card.dark {
  background: #1d1d1f;
  color: white;
}

.card-inner {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  padding: 2rem;
  min-height: 280px;
}

.product-card.large .card-inner {
  min-height: 300px;
}

.product-image {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  max-width: 45%;
}

.product-image img {
  width: 100%;
  height: auto;
  max-height: 220px;
  object-fit: contain;
}

.product-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 0.875rem;
  max-width: 55%;
}

.product-title {
  font-size: 1.75rem;
  font-weight: 300;
  line-height: 1.2;
  margin: 0;
  letter-spacing: -0.02em;
}

.product-title strong {
  font-weight: 600;
}

.product-description {
  font-size: 0.9rem;
  line-height: 1.5;
  color: #6e6e73;
  margin: 0;
}

.product-card.dark .product-description {
  color: #a1a1a6;
}

.shop-button {
  align-self: flex-start;
  padding: 0.65rem 1.75rem;
  background: white;
  border: 2px solid #000;
  border-radius: 2rem;
  font-size: 0.875rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: 0.5rem;
}

.shop-button:hover {
  background: #000;
  color: white;
}

/* Tablet */
@media (max-width: 1024px) {
  .showcase-grid {
    gap: 1rem;
  }

  .card-inner {
    padding: 1.5rem;
    min-height: 240px;
  }

  .product-image img {
    max-height: 180px;
  }

  .product-title {
    font-size: 1.5rem;
  }

  .product-description {
    font-size: 0.85rem;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .product-showcase {
    padding: 1rem 0.5rem;
  }

  .showcase-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .product-card.large,
  .product-card.medium {
    grid-column: span 1;
  }

  .card-inner {
    flex-direction: column;
    padding: 1.5rem;
    text-align: center;
    min-height: auto;
    gap: 1.25rem;
  }

  .product-image {
    max-width: 100%;
    width: 100%;
  }

  .product-image img {
    max-height: 180px;
  }

  .product-content {
    max-width: 100%;
    align-items: center;
  }

  .product-title {
    font-size: 1.5rem;
  }

  .product-description {
    font-size: 0.875rem;
  }

  .shop-button {
    padding: 0.6rem 1.5rem;
    font-size: 0.875rem;
  }
}

/* Small Mobile */
@media (max-width: 480px) {
  .product-showcase {
    padding: 0.75rem 0.5rem;
  }

  .showcase-grid {
    gap: 0.875rem;
  }

  .card-inner {
    padding: 1.25rem;
  }

  .product-image img {
    max-height: 160px;
  }

  .product-title {
    font-size: 1.35rem;
  }

  .product-description {
    font-size: 0.813rem;
  }
}
</style>