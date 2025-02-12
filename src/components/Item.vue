<script setup lang="ts">
type Props = {
  id?: number
  color?: string
  amount?: number
  blurColor?: string,
}

defineProps<Props>()
</script>

<template>
  <div class="item">
    <div class="item__color" :style="{ backgroundColor: color }"></div>
    <span class="item__amount">
      {{ amount }}
    </span>
  </div>
</template>

<style lang="scss" scoped>
.item {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
  cursor: url('@/assets/img/Cursor.svg') 10 10, auto;

  &__color {
    position: relative;
    width: 48px;
    height: 48px;

    &::after {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      bottom: 6px;
      left: 6px;
      backdrop-filter: blur(12px);
    }
  }

  &__amount {
    position: absolute;
    right: 0;
    bottom: 0;
    display: block;
    width: 16px;
    height: 16px;
    border-top: 1px solid var(--border-color);
    border-left: 1px solid var(--border-color);
    border-top-left-radius: 6px;
    font-size: 10px;
    text-align: center;
    // font-weight: 500;
  }
}
</style>
