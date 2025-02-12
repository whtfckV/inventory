<script lang="ts" setup>
import { computed, reactive, ref } from 'vue';
import Card from './Card.vue';
import Cell from './Cell.vue';
import Item from './Item.vue';
import { Transition } from 'vue';
import Information from './Information.vue';

export type Item = {
  id: number,
  color: string,
  amount: number,
}

type Items = (Item | null)[]

const items = reactive<Items>([
  {
    id: 1,
    color: '#7FAA65',
    amount: 4,
  },
  {
    id: 2,
    color: '#AA9765',
    amount: 2,
  },
  {
    id: 3,
    color: '#656CAA',
    amount: 5,
  },
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
  null,
])

const selectedItemId = ref<number>()
const selectedItem = computed(() => items.find(item => item?.id === selectedItemId.value))

const handleClick = (id: number) => {
  selectedItemId.value = id
}

const close = () => {
  selectedItemId.value = 0;
};

</script>

<template>
  <Card class="inventory">
    <Cell v-for="(item, index) in items" :key="index">
      <template v-if="item">
        <Item :key="item.id" :id="item.id" :color="item.color" :amount="item.amount" @click="handleClick(item.id)" />
      </template>
    </Cell>
    <Transition name="slide">
      <Information v-if="selectedItem" @close="close" :item="selectedItem" />
    </Transition>
  </Card>
</template>

<style lang="scss" scoped>
/* Анимация */
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.3s ease-in-out;
}

.slide-enter-from,
.slide-leave-to {
  transform: translateX(100%);
}

.item {
  display: flex;
  height: 100%;
}

.inventory {
  display: grid;
  grid-template-rows: repeat(5, 1fr);
  grid-template-columns: repeat(5, 1fr);
  background-color: var(--border-color);
  gap: 1px;
  padding: 0;
}
</style>
