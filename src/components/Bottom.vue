<script setup lang="ts">
import Card from './Card.vue';
import Sekeleton from './Sekeleton.vue';
</script>

<template>
  <Card :cross="true">
    <Sekeleton :lines="1" max-width="93%" />
  </Card>
</template>
