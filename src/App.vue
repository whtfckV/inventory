<script setup lang="ts">
import Bottom from './components/Bottom.vue';
import Inventory from './components/Inventory.vue';
import Preview from './components/Preview.vue';

</script>

<template>
  <main class="main">
    <div class="container grid">
      <Preview />
      <Inventory />
      <Bottom class="main__bottom" />
      <!-- <div class="main__bottom card">
        <Sekeleton :lines="1" max-width="93%" />
      </div> -->
    </div>
  </main>
</template>

<style lang="scss" scoped>
.grid {
  display: grid;
  grid-template-rows: 1fr 72px;
  grid-template-columns: 236px 1fr;
  gap: var(--gap);

  &__container {
    display: grid;
    grid-template-columns: subgrid;
  }

}

.main {
  margin: 32px 0;

  &__bottom {
    grid-column: span 2;
  }
}
</style>
