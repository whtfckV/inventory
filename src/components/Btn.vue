<script setup lang="ts">
type Props = {
  type?: 'icon' | 'text'
  color?: 'red' | 'white'
  size?: 'small' | 'medium'
}

defineProps<Props>()

</script>

<template>
  <button :class="['btn', `btn--${type}`, `btn--${color}`, `btn--${size}`]">
    <slot />
  </button>
</template>

<style lang="scss" scoped>
.btn {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
  border: none;
  padding: 0;
  background-color: transparent;
  cursor: pointer;

  &--icon {
    width: 24px;
    height: 24px;
  }

  &--text {
    width: 100%;
    border-radius: 8px;
    font-weight: 400;
    font-size: 14px;
    letter-spacing: 0;
    color: #ffffff;
    text-align: center;
  }

  &--red {
    background: #FA7272;
  }

  &--white {
    background-color: #ffffff;
  }

  &--small {
    font-size: 12px;
    line-height: 16px;
  }

  &--medium {
    padding: 11px 0;
  }

}
</style>
