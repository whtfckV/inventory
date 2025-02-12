<script setup lang="ts">
import { mdiClose } from '@mdi/js';
import Btn from './Btn.vue';
type Props = {
  cross?: boolean
}

withDefaults(defineProps<Props>(), {
  cross: false,
})
</script>

<template>
  <div class="card">
    <Btn type="icon" v-if="cross" class="card__close">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="#ffffff">
        <path :d="mdiClose" />
      </svg>
    </Btn>
    <slot />
  </div>
</template>

<style lang="scss" scoped>
.card {
  position: relative;
  border-radius: 12px;
  border: 1px solid var(--border-color);
  padding: 18px;
  background-color: var(--color-bg-card);
  overflow: hidden;

  &__close {
    position: absolute;
    top: 8px;
    right: 8px;
  }
}
</style>
