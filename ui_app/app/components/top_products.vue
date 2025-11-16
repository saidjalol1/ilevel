<template>
  <div class="popular-products">
    <div class="products-grid">
      <!-- Popular Products Card -->
      <div class="product-card">
        <div class="product-image">
          <img src="https://images.unsplash.com/photo-1598327105666-5b89351aff97?w=400&h=300&fit=crop" alt="Mashhur Mahsulotlar" />
        </div>
        <h2 class="product-title">Mashhur Mahsulotlar</h2>
        <p class="product-description">
          iPad ajoyib 10.2 dyuymli Retina displey, aql bovar qilmaydigan ishlash, 
          ko'p vazifalilik va foydalanish qulayligini birlashtiradi.
        </p>
        <button class="shop-button">Xarid qilish</button>
      </div>

      <!-- iPad Pro Card -->
      <div class="product-card">
        <div class="product-image">
          <img src="https://images.unsplash.com/photo-1544244015-0df4b3ffc6b0?w=400&h=300&fit=crop" alt="iPad Pro" />
        </div>
        <h2 class="product-title">iPad Pro</h2>
        <p class="product-description">
          iPad ajoyib 10.2 dyuymli Retina displey, aql bovar qilmaydigan ishlash, 
          ko'p vazifalilik va foydalanish qulayligini birlashtiradi.
        </p>
        <button class="shop-button">Xarid qilish</button>
      </div>

      <!-- Samsung Galaxy Card -->
      <div class="product-card">
        <div class="product-image">
          <img src="https://images.unsplash.com/photo-1610945415295-d9bbf067e59c?w=400&h=300&fit=crop" alt="Samsung Galaxy" />
        </div>
        <h2 class="product-title">Samsung Galaxy</h2>
        <p class="product-description">
          iPad ajoyib 10.2 dyuymli Retina displey, aql bovar qilmaydigan ishlash, 
          ko'p vazifalilik va foydalanish qulayligini birlashtiradi.
        </p>
        <button class="shop-button">Xarid qilish</button>
      </div>

      <!-- Macbook Pro Card -->
      <div class="product-card dark-card">
        <div class="product-image">
          <img src="https://images.unsplash.com/photo-1517336714731-489689fd1ca8?w=400&h=300&fit=crop" alt="Macbook Pro" />
        </div>
        <h2 class="product-title">Macbook Pro</h2>
        <p class="product-description">
          iPad ajoyib 10.2 dyuymli Retina displey, aql bovar qilmaydigan ishlash, 
          ko'p vazifalilik va foydalanish qulayligini birlashtiradi.
        </p>
        <button class="shop-button dark-button">Xarid qilish</button>
      </div>
    </div>
  </div>
</template>

<script setup>
// Nuxt 3 component - no additional logic needed for this static version
</script>

<style scoped>
.popular-products {
  width: 100%;
  padding: 40px 20px;
  background-color: #f5f5f5;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  max-width: 1400px;
  margin: 0 auto;
}

.product-card {
  background: white;
  border-radius: 8px;
  padding: 30px 25px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.12);
}

.dark-card {
  background: #1a1a1a;
  color: white;
}

.product-image {
  width: 100%;
  height: 200px;
  margin-bottom: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.product-image img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.product-title {
  font-size: 24px;
  font-weight: 600;
  margin-bottom: 15px;
  color: inherit;
}

.product-description {
  font-size: 14px;
  line-height: 1.6;
  color: #666;
  margin-bottom: 25px;
  flex-grow: 1;
}

.dark-card .product-description {
  color: #b0b0b0;
}

.shop-button {
  padding: 12px 32px;
  border: 2px solid #000;
  background: transparent;
  border-radius: 6px;
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  color: #000;
}

.shop-button:hover {
  background: #000;
  color: white;
}

.dark-button {
  border-color: white;
  color: white;
}

.dark-button:hover {
  background: white;
  color: #000;
}

@media (max-width: 768px) {
  .products-grid {
    grid-template-columns: 1fr;
  }
  
  .popular-products {
    padding: 20px 15px;
  }
}
</style>