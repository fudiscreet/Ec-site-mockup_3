<template>
    <div class="container mx-auto px-4 py-8">
      <h2 class="text-2xl font-bold mb-6">チェックアウト</h2>
      <div class="flex flex-col md:flex-row">
        <div class="md:w-1/2 pr-4">
          <h3 class="text-xl font-semibold mb-4">注文内容</h3>
          <div v-for="item in cartItems" :key="item.id" class="flex items-center mb-4">
            <img :src="item.image" :alt="item.name" class="w-16 h-16 object-cover rounded mr-4"/>
            <div>
              <h4 class="font-semibold">{{ item.name }}</h4>
              <p>¥{{ item.price.toLocaleString() }} × {{ item.quantity }}</p>
            </div>
          </div>
          <div class="mt-4">
            <p class="flex justify-between"><span>小計:</span><span>¥{{ subtotal.toLocaleString() }}</span></p>
            <p class="flex justify-between"><span>送料:</span><span>¥{{ shippingFee.toLocaleString() }}</span></p>
            <p class="flex justify-between font-semibold"><span>合計:</span><span>¥{{ total.toLocaleString() }}</span></p>
          </div>
        </div>
        <div class="md:w-1/2 pl-4 mt-8 md:mt-0">
          <h3 class="text-xl font-semibold mb-4">配送情報</h3>
          <form @submit.prevent="placeOrder">
            <div class="mb-4">
              <label class="block mb-2">氏名</label>
              <input v-model="shippingInfo.name" type="text" required class="border rounded px-4 py-2 w-full"/>
            </div>
            <div class="mb-4">
              <label class="block mb-2">電話番号</label>
              <input v-model="shippingInfo.phone" type="tel" required class="border rounded px-4 py-2 w-full"/>
            </div>
            <div class="mb-4">
              <label class="block mb-2">郵便番号</label>
              <input v-model="shippingInfo.postalCode" type="text" required class="border rounded px-4 py-2 w-full"/>
            </div>
            <div class="mb-4">
              <label class="block mb-2">住所</label>
              <input v-model="shippingInfo.address" type="text" required class="border rounded px-4 py-2 w-full"/>
            </div>
            <div class="mb-4">
              <label class="block mb-2">メールアドレス</label>
              <input v-model="shippingInfo.email" type="email" required class="border rounded px-4 py-2 w-full"/>
            </div>
            <div class="mb-4">
              <label class="block mb-2">配送希望日</label>
              <input v-model="shippingInfo.deliveryDate" type="date" required class="border rounded px-4 py-2 w-full"/>
            </div>
            <h3 class="text-xl font-semibold mb-4">支払い情報</h3>
            <div class="mb-4">
              <label class="block mb-2">支払い方法</label>
              <select v-model="paymentMethod" required class="border rounded px-4 py-2 w-full">
                <option value="">選択してください</option>
                <option value="credit_card">クレジットカード</option>
                <option value="bank_transfer">銀行振込</option>
              </select>
            </div>
            <button type="submit" class="bg-blue-500 text-white px-6 py-2 rounded hover:bg-blue-600">
              注文を確定する
            </button>
          </form>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CheckoutPage',
    data() {
      return {
        cartItems: [
          { id: 1, name: '商品名', price: 2299, quantity: 1, image: '/placeholder.jpg' }
        ],
        shippingFee: 500,
        shippingInfo: {
          name: '',
          phone: '',
          postalCode: '',
          address: '',
          email: '',
          deliveryDate: ''
        },
        paymentMethod: ''
      }
    },
    computed: {
      subtotal() {
        return this.cartItems.reduce((total, item) => total + item.price * item.quantity, 0);
      },
      total() {
        return this.subtotal + this.shippingFee;
      }
    },
    methods: {
      placeOrder() {
        // 注文処理のロジックをここに実装
        console.log('注文が確定されました', {
          items: this.cartItems,
          shippingInfo: this.shippingInfo,
          paymentMethod: this.paymentMethod,
          total: this.total
        });
        // 注文完了ページへリダイレクト
        this.$router.push('/order-complete');
      }
    }
  }
  </script>