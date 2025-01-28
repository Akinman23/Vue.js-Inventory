<template>
    <div class="modal-overlay">
      <div class="modal">
        <h2>{{ item.name }}</h2>
        <p>{{ item.description }}</p>
        <button @click="$emit('delete', item)">Delete</button>
        <button @click="$emit('close')">Close</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['item'],
  };
  </script>
  
  <style>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .modal {
    background: white;
    padding: 16px;
    border-radius: 8px;
  }
  </style>
  