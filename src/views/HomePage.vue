<template>
    <div class="container mx-auto px-4 py-8">
      <h2 class="text-2xl font-bold mb-4">{ ECサイト名 }へようこそ</h2>
      <section class="mb-8">
        <h3 class="text-xl font-semibold mb-4">カテゴリー</h3>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div v-for="category in categories" :key="category.id" class="border rounded-lg p-4">
            <div class="aspect-w-16 aspect-h-9 mb-2">
              <img :src="category.image" :alt="category.name" class="object-cover rounded-lg">
            </div>
            <p class="text-center">{{ category.name }}</p>
          </div>
        </div>
      </section>
      <section class="mb-8">
        <h3 class="text-xl font-semibold mb-4">おすすめ商品</h3>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div v-for="item in recommendedItems" :key="item.id" class="border rounded-lg p-4">
            <div class="aspect-w-16 aspect-h-9 mb-2">
              <img :src="item.image" :alt="item.name" class="object-cover rounded-lg">
            </div>
            <p class="font-semibold">{{ item.name }}</p>
            <p class="text-gray-600">¥{{ item.price.toLocaleString() }}</p>
          </div>
        </div>
      </section>
      <section>
        <h3 class="text-xl font-semibold mb-4">セール</h3>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div v-for="item in saleItems" :key="item.id" class="border rounded-lg p-4">
            <div class="aspect-w-16 aspect-h-9 mb-2">
              <img :src="item.image" :alt="item.name" class="object-cover rounded-lg">
            </div>
            <p class="font-semibold">{{ item.name }}</p>
            <p class="text-gray-600 line-through">¥{{ item.originalPrice.toLocaleString() }}</p>
            <p class="text-red-600 font-bold">¥{{ item.salePrice.toLocaleString() }}</p>
          </div>
        </div>
      </section>
    </div>
  </template>
  
  <script>
  export default {
    name: 'HomePage',
    data() {
      return {
        categories: [
          { id: 1, name: 'カテゴリー1', image: '/placeholder.jpg' },
          { id: 2, name: 'カテゴリー2', image: '/placeholder.jpg' },
          { id: 3, name: 'カテゴリー3', image: '/placeholder.jpg' },
        ],
        recommendedItems: [
          { id: 1, name: 'アイテム1', price: 3300, image: '/placeholder.jpg' },
          { id: 2, name: 'アイテム2', price: 4500, image: '/placeholder.jpg' },
          { id: 3, name: 'アイテム3', price: 6200, image: '/placeholder.jpg' },
        ],
        saleItems: [
          { id: 1, name: 'セールアイテム1', originalPrice: 5000, salePrice: 3500, image: '/placeholder.jpg' },
          { id: 2, name: 'セールアイテム2', originalPrice: 8000, salePrice: 6000, image: '/placeholder.jpg' },
        ],
      }
    }
  }
  </script>