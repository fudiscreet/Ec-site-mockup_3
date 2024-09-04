<template>
  <div class="container mx-auto px-4 py-8">
    <h2 class="text-2xl font-bold mb-6">{ ECサイト名 }へようこそ</h2>
    <section class="mb-8">
      <h3 class="text-xl font-semibold mb-4">カテゴリー</h3>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div v-for="category in categories" :key="category.id" class="border rounded-lg p-4">
          <div class="aspect-w-16 aspect-h-9 mb-2 bg-gray-200">
            <!-- プレースホルダー画像 -->
            <div class="flex items-center justify-center h-full text-gray-500">
              カテゴリー画像
            </div>
          </div>
          <p class="text-center">{{ category.name }}</p>
        </div>
      </div>
    </section>
    <section class="mb-8">
      <h3 class="text-xl font-semibold mb-4">おすすめ商品</h3>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div v-for="item in recommendedItems" :key="item.id" class="border rounded-lg p-4">
          <div class="aspect-w-16 aspect-h-9 mb-2 bg-gray-200">
            <!-- プレースホルダー画像 -->
            <div class="flex items-center justify-center h-full text-gray-500">
              商品画像
            </div>
          </div>
          <p class="font-semibold">{{ item.name }}</p>
          <p class="text-gray-600">¥{{ item.price.toLocaleString() }}</p>
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
        { id: 1, name: 'カテゴリー1' },
        { id: 2, name: 'カテゴリー2' },
        { id: 3, name: 'カテゴリー3' },
      ],
      recommendedItems: [
        { id: 1, name: 'アイテム1', price: 3300 },
        { id: 2, name: 'アイテム2', price: 4500 },
        { id: 3, name: 'アイテム3', price: 6200 },
      ],
    }
  }
}
</script>