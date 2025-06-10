<template>
  <div class="my-5">
    <h3>Lista de regalos</h3>
    <ul class="list-unstyled">
      <li v-for="(list, index) in giftLists" :key="index">
        <a :href="list.url" target="_blank" rel="noopener" class="btn btn-outline-success m-2">
          {{ list.name }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script setup>
const giftLists = [
  { name: 'Amazon', url: 'https://www.amazon.com.mx/hz/wishlist/ls/EXAMPLE' },
  { name: 'Liverpool', url: 'https://www.liverpool.com.mx/tienda/registro-de-deseos?example' },
]
</script>
