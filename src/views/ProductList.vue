<template>
    <div class="container mx-auto px-4 py-8">
      <h2 class="text-2xl font-bold mb-6">商品一覧</h2>
      <div class="flex mb-4">
        <input
          v-model="searchQuery"
          type="text"
          placeholder="商品を検索"
          class="border rounded-l px-4 py-2 w-full"
        />
        <button class="bg-blue-500 text-white px-4 py-2 rounded-r">検索</button>
      </div>
      <div class="flex mb-4">
        <div class="w-1/4 pr-4">
          <h3 class="font-semibold mb-2">カテゴリー</h3>
          <div v-for="category in categories" :key="category.id" class="mb-2">
            <label class="flex items-center">
              <input type="checkbox" :value="category.id" v-model="selectedCategories" class="mr-2"/>
              {{ category.name }}
            </label>
          </div>
        </div>
        <div class="w-3/4">
          <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
            <div v-for="product in filteredProducts" :key="product.id" class="border rounded-lg p-4">
              <div class="aspect-w-16 aspect-h-9 mb-2">
                <img :src="product.image" :alt="product.name" class="object-cover rounded-lg"/>
              </div>
              <h3 class="font-semibold">{{ product.name }}</h3>
              <p class="text-gray-600" v-if="product.originalPrice">
                <span class="line-through">¥{{ product.originalPrice.toLocaleString() }}</span>
                <span class="text-red-600 font-bold ml-2">¥{{ product.price.toLocaleString() }}</span>
              </p>
              <p class="text-gray-600" v-else>¥{{ product.price.toLocaleString() }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductList',
    data() {
      return {
        searchQuery: '',
        selectedCategories: [],
        categories: [
          { id: 1, name: 'キッチン' },
          { id: 2, name: 'インテリア' },
          { id: 3, name: 'ステーショナリー' },
        ],
        products: [
          { id: 1, name: 'キッチンアイテム1', price: 2200, originalPrice: 3300, image: '/placeholder.jpg', categoryId: 1 },
          { id: 2, name: 'キッチンアイテム3', price: 4210, originalPrice: 7400, image: '/placeholder.jpg', categoryId: 1 },
          { id: 3, name: 'キッチンアイテム5', price: 1299, image: '/placeholder.jpg', categoryId: 1 },
          { id: 4, name: 'キッチンアイテム8', price: 1399, image: '/placeholder.jpg', categoryId: 1 },
          { id: 5, name: 'キッチンアイテム9', price: 1200, image: '/placeholder.jpg', categoryId: 1 },
          { id: 6, name: 'キッチンアイテム10', price: 1203, image: '/placeholder.jpg', categoryId: 1 },
        ]
      }
    },
    computed: {
      filteredProducts() {
        return this.products.filter(product => {
          const matchesSearch = product.name.toLowerCase().includes(this.searchQuery.toLowerCase());
          const matchesCategory = this.selectedCategories.length === 0 || this.selectedCategories.includes(product.categoryId);
          return matchesSearch && matchesCategory;
        });
      }
    }
  }
  </script>