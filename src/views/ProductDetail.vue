<template>
    <div class="container mx-auto px-4 py-8">
      <div class="flex flex-col md:flex-row">
        <div class="md:w-1/2 pr-4">
          <img :src="product.image" :alt="product.name" class="w-full rounded-lg"/>
        </div>
        <div class="md:w-1/2 pl-4">
          <h2 class="text-2xl font-bold mb-4">{{ product.name }}</h2>
          <p class="text-xl mb-4">¥{{ product.price.toLocaleString() }}</p>
          <p class="mb-4">{{ product.description }}</p>
          <div class="mb-4">
            <label class="block mb-2">数量</label>
            <input v-model.number="quantity" type="number" min="1" class="border rounded px-4 py-2 w-20"/>
          </div>
          <button @click="addToCart" class="bg-blue-500 text-white px-6 py-2 rounded hover:bg-blue-600">
            カートに追加
          </button>
        </div>
      </div>
      <div class="mt-8">
        <h3 class="text-xl font-semibold mb-4">カスタマーレビュー</h3>
        <div v-for="review in reviews" :key="review.id" class="mb-4 p-4 bg-gray-100 rounded-lg">
          <div class="flex items-center mb-2">
            <div class="font-semibold mr-2">{{ review.author }}</div>
            <div class="text-yellow-500">{{ '★'.repeat(review.rating) }}</div>
          </div>
          <p>{{ review.content }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductDetail',
    data() {
      return {
        product: {
          id: 1,
          name: '{商品名}',
          price: 2999,
          description: '商品の詳細な説明がここに入ります。',
          image: '/placeholder.jpg'
        },
        quantity: 1,
        reviews: [
          { id: 1, author: 'レビュアー1', rating: 5, content: 'とても良い商品です。' },
          { id: 2, author: 'レビュアー2', rating: 4, content: '使いやすくて気に入っています。' }
        ]
      }
    },
    methods: {
      addToCart() {
        // カートに商品を追加する処理
        console.log(`${this.product.name} を ${this.quantity} 個カートに追加しました。`);
        // 実際にはここでVuexのアクションを呼び出すなどしてカートの状態を更新します
      }
    }
  }
  </script>