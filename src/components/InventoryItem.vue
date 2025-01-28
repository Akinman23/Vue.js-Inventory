<template>
    <div class="inventory-item" @click="$emit('click')">
      <img :src="item.image || '/default-item.png'" alt="Item Image" />
      <p>{{ item.name }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['item'],
  };
  </script>
  
  <style>
  .inventory-item {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: center;
    cursor: pointer;
  }
  .inventory-item img {
    width: 100%;
    height: auto;
  }
  </style>
  