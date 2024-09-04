<template>
    <div class="container mx-auto px-4 py-8">
      <h2 class="text-2xl font-bold mb-6">ショッピングカート</h2>
      <div v-if="cartItems.length > 0">
        <div v-for="item in cartItems" :key="item.id" class="flex items-center border-b py-4">
          <img :src="item.image" :alt="item.name" class="w-16 h-16 object-cover rounded mr-4"/>
          <div class="flex-grow">
            <h3 class="font-semibold">{{ item.name }}</h3>
            <p class="text-gray-600">¥{{ item.price.toLocaleString() }}</p>
          </div>
          <div class="flex items-center">
            <button @click="decreaseQuantity(item)" class="px-2 py-1 border rounded">-</button>
            <span class="mx-2">{{ item.quantity }}</span>
            <button @click="increaseQuantity(item)" class="px-2 py-1 border rounded">+</button>
          </div>
          <button @click="removeItem(item)" class="ml-4 text-red-500">削除</button>
        </div>
        <div class="mt-6 text-right">
          <p class="text-xl font-semibold">合計: ¥{{ totalPrice.toLocaleString() }}</p>
          <button @click="proceedToCheckout" class="mt-4 bg-blue-500 text-white px-6 py-2 rounded hover:bg-blue-600">
            チェックアウトへ進む
          </button>
        </div>
      </div>
      <div v-else class="text-center py-8">
        <p>カートは空です。</p>
        <router-link to="/" class="text-blue-500 hover:underline">ショッピングを続ける</router-link>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ShoppingCart',
    data() {
      return {
        cartItems: [
          { id: 1, name: '商品名', price: 2239, quantity: 1, image: '/placeholder.jpg' }
        ]
      }
    },
    computed: {
      totalPrice() {
        return this.cartItems.reduce((total, item) => total + item.price * item.quantity, 0);
      }
    },
    methods: {
      decreaseQuantity(item) {
        if (item.quantity > 1) {
          item.quantity--;
        }
      },
      increaseQuantity(item) {
        item.quantity++;
      },
      removeItem(item) {
        const index = this.cartItems.indexOf(item);
        if (index > -1) {
          this.cartItems.splice(index, 1);
        }
      },
      proceedToCheckout() {
        // チェックアウトページへ遷移
        this.$router.push('/checkout');
      }
    }
  }
  </script>