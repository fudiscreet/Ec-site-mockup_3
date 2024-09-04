<template>
    <div class="container mx-auto px-4 py-8">
      <div class="max-w-md mx-auto bg-white shadow-md rounded-lg overflow-hidden">
        <div class="p-6">
          <h2 class="text-2xl font-bold text-center mb-4">ご注文ありがとうございます！</h2>
          <p class="text-center mb-4">注文が正常に完了しました。</p>
          <div class="bg-gray-100 rounded-lg p-4 mb-4">
            <p class="mb-2"><span class="font-semibold">注文ID：</span> {{ orderId }}</p>
            <p><span class="font-semibold">注文日時：</span> {{ orderDate }}</p>
          </div>
          <div class="flex flex-col space-y-2">
            <button @click="viewOrder" class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded">
              注文を確認する
            </button>
            <button @click="continueShopping" class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded">
              ショッピングを続ける
            </button>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'OrderComplete',
    data() {
      return {
        orderId: 'ORD-xxxxxxxxxxxxx',
        orderDate: new Date().toLocaleString('ja-JP', { year: 'numeric', month: '2-digit', day: '2-digit' })
      }
    },
    methods: {
      viewOrder() {
        // 注文詳細ページへ遷移
        this.$router.push({ name: 'OrderDetail', params: { id: this.orderId } })
      },
      continueShopping() {
        // ホームページへ遷移
        this.$router.push({ name: 'Home' })
      }
    }
  }
  </script>