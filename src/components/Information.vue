<script setup lang="ts">
import type { Item } from './Inventory.vue';
import { mdiClose } from '@mdi/js';
import Sekeleton from './Sekeleton.vue';
import Btn from './Btn.vue';
import { ref } from 'vue';

type Props = {
  item?: Item
}

defineProps<Props>()
const emit = defineEmits(['close'])
const isDeliting = ref(false)
const deleteAmount = ref()

const handleDelete = () => {
  isDeliting.value = true
}

const close = () => {
  emit('close')
}

</script>

<template>
  <div class="panel">
    <Btn type="icon" @click="close" class="panel__close">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="#ffffff">
        <path :d="mdiClose" />
      </svg>
    </Btn>
    <div class="item">
      <div class="item__color" :style="{ backgroundColor: item?.color }"></div>
    </div>
    <hr class="divider">
    <div class="panel__info">
      <Sekeleton :lines="1" height="26px" radius="8px" />
      <div class='panel__descr'>
        <Sekeleton :lines="1" max-width="211px" height="10px" radius="4px" />
        <Sekeleton :lines="1" max-width="211px" height="10px" radius="4px" />
        <Sekeleton :lines="1" max-width="211px" height="10px" radius="4px" />
        <Sekeleton :lines="1" max-width="180px" height="10px" radius="4px" />
      </div>
      <Sekeleton :lines="1" max-width="80px" height="10px" radius="4px" />
    </div>
    <hr class="divider">
    <template v-if="isDeliting">
      <div class="panel__actions">
        <input class="panel__input" type="text" v-model="deleteAmount">
        <Btn>
          Отмена
        </Btn>
        <Btn>
          Подтвердить
        </Btn>
      </div>
    </template>
    <Btn v-else class="panel__delete" type="text" size="medium" color="red" @click="handleDelete">Удалить предмет</Btn>
  </div>
</template>

<style lang="scss" scoped>
.panel {
  position: absolute;
  top: 0;
  right: 0;
  padding: 15px 18px;
  padding-top: 55px;
  border-left: 1px solid var(--border-color);
  width: 250px;
  height: 100%;
  z-index: 1;
  backdrop-filter: blur(16px);

  &__actions {
    display: grid;
    grid-template-columns: 88px 112px;
    row-gap: 20px;
    column-gap: 10px;
    margin-top: 20px;
  }

  &__input {
    grid-column: span 2;
    border: 1px solid var(--border-color);
    border-radius: 4px;
    // padding: 10px;
    height: 40px;
  }

  &__info {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 24px;
    padding-top: 16px;
    padding-bottom: 24px;
    min-height: 198px;
  }

  &__descr {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    gap: 16px;
  }

  &__close {
    position: absolute;
    top: 8px;
    right: 8px;
  }

  &__delete {
    margin-top: 18px;
  }
}

.divider {
  border-color: #4D4D4D;
  border-width: 1px;
}

.item {
  display: flex;
  justify-content: center;
  margin-bottom: 30px;

  &__color {
    position: relative;
    width: 115.56px;
    height: 115.56px;

    &::after {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      bottom: 14.44px;
      left: 14.44px;
      backdrop-filter: blur(12px);
    }
  }
}
</style>
