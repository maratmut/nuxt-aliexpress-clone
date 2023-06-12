<template>
  <MainLayout>
    <div class="mt-4 max-w-[1200px] mx-auto px-2">
      <div
        class="grid xl:grid-cols-6 lg:grid-cols-5 md:grid-cols-4 sm:grid-cols-3 grid-cost-2 gap-4"
      >
        <div v-if="products" v-for="product in products" :key="product">
          <ProductComponent :product="product" />
        </div>
      </div>
    </div>
  </MainLayout>
</template>

<script setup>
import MainLayout from '~/layouts/MainLayout.vue';
import ProductComponent from '~/components/ProductComponent.vue'

const products = [
    {id: 1, title: 'Заголовок 1', description: 'Это описание', url: 'https://picsum.photos/id/7/800/800', price: 9999 },
    {id: 2, title: 'Заголовок 2', description: 'Это описание', url: 'https://picsum.photos/id/71/800/800', price: 3299 },
    {id: 3, title: 'Заголовок 3', description: 'Это описание', url: 'https://picsum.photos/id/72/800/800', price: 2299 },
    {id: 4, title: 'Заголовок 4', description: 'Это описание', url: 'https://picsum.photos/id/73/800/800', price: 1299 },
    {id: 5, title: 'Заголовок 5', description: 'Это описание', url: 'https://picsum.photos/id/74/800/800', price: 6799 },
    {id: 6, title: 'Заголовок 6', description: 'Это описание', url: 'https://picsum.photos/id/75/800/800', price: 9695 },
    {id: 7, title: 'Заголовок 7', description: 'Это описание', url: 'https://picsum.photos/id/76/800/800', price: 1199 },
    {id: 8, title: 'Заголовок 8', description: 'Это описание', url: 'https://picsum.photos/id/77/800/800', price: 979 },
    {id: 9, title: 'Заголовок 9', description: 'Это описание', url: 'https://picsum.photos/id/78/800/800', price: 999 },
    {id: 10, title: 'Заголовок 10', description: 'Это описание', url: 'https://picsum.photos/id/79/800/800', price: 6690 }
]
</script>
