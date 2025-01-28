<template>
    <div class="inventory-grid">
      <draggable v-model="items" @end="saveToLocalStorage">
        <InventoryItem
          v-for="(item, index) in items"
          :key="index"
          :item="item"
          @click="selectItem(item)"
        />
      </draggable>
      <ItemDetailsModal
        v-if="selectedItem"
        :item="selectedItem"
        @close="selectedItem = null"
        @delete="deleteItem"
      />
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  import draggable from 'vuedraggable';
  import InventoryItem from './InventoryItem.vue';
  import ItemDetailsModal from './ItemDetailsModal.vue';
  import { loadFromLocalStorage, saveToLocalStorage } from '../utils/storage.js';
  
  export default {
    components: { draggable, InventoryItem, ItemDetailsModal },
    setup() {
      const items = ref(loadFromLocalStorage('inventory') || []);
      const selectedItem = ref(null);
  
      const selectItem = (item) => (selectedItem.value = item);
      const deleteItem = (item) => {
        items.value = items.value.filter((i) => i !== item);
        saveToLocalStorage('inventory', items.value);
        selectedItem.value = null;
      };
  
      const saveToLocalStorage = () => {
        saveToLocalStorage('inventory', items.value);
      };
  
      return { items, selectedItem, selectItem, deleteItem, saveToLocalStorage };
    },
  };
  </script>
  
  <style>
  .inventory-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 16px;
    padding: 16px;
  }
  </style>
  