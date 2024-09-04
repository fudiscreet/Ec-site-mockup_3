<template>
    <div class="container mx-auto px-4 py-8">
      <h2 class="text-2xl font-bold mb-6">注文履歴</h2>
      <div v-for="order in orders" :key="order.id" class="bg-white shadow-md rounded-lg overflow-hidden mb-4">
        <div class="p-6">
          <h3 class="text-xl font-semibold mb-2">注文 #{{ order.id }}</h3>
          <div class="grid grid-cols-2 gap-4">
            <div>
              <h4 class="font-semibold mb-1">注文内容</h4>
              <p>{{ order.productName }} × {{ order.quantity }}</p>
              <p class="font-semibold mt-2">小計: ¥{{ order.subtotal.toLocaleString() }}</p>
              <p>送料: ¥{{ order.shippingFee.toLocaleString() }}</p>
              <p class="font-semibold">合計: ¥{{ order.total.toLocaleString() }}</p>
            </div>
            <div>
              <h4 class="font-semibold mb-1">配送情報</h4>
              <p>配送先: {{ order.shippingAddress }}</p>
              <p>配送予定日: {{ order.estimatedDeliveryDate }}</p>
              <h4 class="font-semibold mt-2 mb-1">支払い情報</h4>
              <p>支払い方法: {{ order.paymentMethod }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'OrderHistory',
    data() {
      return {
        orders: [
          {
            id: 'ORD-xxxxxxxxxxxxx',
            productName: '{商品名}',
            quantity: 1,
            subtotal: 2299,
            shippingFee: 500,
            total: 2799,
            shippingAddress: '{名前}\n{住所}',
            estimatedDeliveryDate: 'yyyy年mm月dd日',
            paymentMethod: '銀行振込'
          }
          // 他の注文履歴をここに追加
        ]
      }
    }
  }
  </script>