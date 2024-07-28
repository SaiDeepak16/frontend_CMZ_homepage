<template>
    <div class="products-container mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-8">
      <div class="products-grid">
        <ProductCard
          v-for="product in visibleProducts"
          :key="product.id"
          :image="product.image"
          :title="product.title"
          :rating="product.rating"
          :reviews="product.reviews"
          :price="product.price"
          :showDescription="false"
          class="product-card"
        />
      </div>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { computed } from 'vue';
  import ProductCard from './product.vue';
  
  const products = [
    {
      id: 1,
      image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/sneakers.png',
      title: 'Athletic mens walking sneakers',
      rating: 5,
      reviews: 123,
      price: '$2345.99'
    },
    {
      id: 2,
      image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/sneakers.png',
      title: 'Stylish womens running shoes',
      rating: 4,
      reviews: 98,
      price: '$199.99'
    },
    {
      id: 3,
      image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/sneakers.png',
      title: 'Kids sporty sneakers',
      rating: 4.5,
      reviews: 76,
      price: '$129.99'
    },
    {
      id: 4,
      image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/sneakers.png',
      title: 'High-performance trail running shoes',
      rating: 4.7,
      reviews: 89,
      price: '$349.99'
    },
    {
      id: 5,
      image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/sneakers.png',
      title: 'Comfortable daily wear shoes',
      rating: 4.3,
      reviews: 54,
      price: '$179.99'
    },
    {
      id: 6,
      image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/sneakers.png',
      title: 'Elegant formal shoes',
      rating: 4.8,
      reviews: 120,
      price: '$299.99'
    }
  ];
  
  const isMobile = computed(() => window.innerWidth < 768);
  const visibleProducts = computed(() => {
    return isMobile.value ? products.slice(0, 4) : products.slice(0, 5);
  });
  </script>
  
  <style scoped>
  .products-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .products-grid {
    display: grid;
    gap: 1rem;
    grid-template-columns: repeat(1, minmax(0, 1fr));
    width: 100%;
  }
  
  
  
   @media (min-width: 1024px) {
    .products-grid {
      grid-template-columns: repeat(5, minmax(0, 1fr));
    }
  }

  
  @media (max-width: 650px) {
    .products-grid {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }
  }
  .product-card {
    width: 100%;
    max-width: 300px;
    margin: 0 auto;
  }
  </style>
  