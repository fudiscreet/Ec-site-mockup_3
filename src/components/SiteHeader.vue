<template>
    <header class="bg-white shadow-md">
      <div class="container mx-auto px-4 py-2 flex justify-between items-center">
        <router-link to="/" class="text-xl font-bold">{ ECサイト名 }</router-link>
        <nav>
          <ul class="flex space-x-4">
            <li><router-link to="/products" class="hover:text-gray-600">商品一覧</router-link></li>
            <li><router-link to="/order-history" class="hover:text-gray-600">注文履歴</router-link></li>
            <li>
              <router-link to="/cart" class="relative">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
                </svg>
              </router-link>
            </li>
          </ul>
        </nav>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    name: 'SiteHeader'
  }
  </script>