<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  lines?: number
  maxWidth?: string
  animated?: boolean
  height?: string
  radius?: string
}

const props = withDefaults(defineProps<Props>(), {
  lines: 3,
  maxWidth: '100%',
  animated: true,
  height: '100%',
  radius: '12px',
})

const lineStyles = computed(() =>
  Array.from({ length: props.lines }, (_, index) => {
    const width = index === props.lines - 1 ? props.maxWidth : `${Math.random() * 70 + 30}%`
    const borderRadius = index === props.lines - 1 ? props.radius : `${Math.random() * 70 + 30}%`
    return { width, borderRadius }
  })
)
</script>

<template>
  <div class="skeleton" :style="{ height: props.height, ...style }" v-for="(style, index) in lineStyles">
    <div :key="index" class="skeleton-line" :class="{ animated: props.animated }"
      :style="{ borderRadius: style.borderRadius }"></div>
  </div>
</template>

<style scoped>
.skeleton {
  display: flex;
  flex-direction: column;
  /* align-items: center; */
  width: 100%;
  gap: 8px;
}

.skeleton-line {
  flex: 1;
  background: #444444;
}

.animated {
  animation: shimmer 1.5s infinite linear;
  background: linear-gradient(90deg, #3C3C3C 25%, #444444 50%, #333333 75%);
  background-size: 200% 100%;
}

@keyframes shimmer {
  0% {
    background-position: -200% 0;
  }

  100% {
    background-position: 200% 0;
  }
}
</style>
