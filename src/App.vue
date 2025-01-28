<template>
  <div :class="theme">
    <header>
      <h1>Inventory</h1>
      <ThemeToggle @toggle="toggleTheme" />
    </header>
    <InventoryGrid />
  </div>
</template>

<script>
import { ref } from 'vue';
import InventoryGrid from './components/InventoryGrid.vue';
import ThemeToggle from './components/ThemeToggle.vue';

export default {
  components: { InventoryGrid, ThemeToggle },
  setup() {
    const theme = ref('light'); // Default theme
    const toggleTheme = () => {
      theme.value = theme.value === 'light' ? 'dark' : 'light';
    };

    return { theme, toggleTheme };
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
</style>
