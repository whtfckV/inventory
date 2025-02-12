<script setup lang="ts">
import Card from './Card.vue';
import Sekeleton from './Sekeleton.vue';
</script>

<template>
  <Card class="preview">
    <!--
    Можно было бы сделать picture и под разные разрешения и
    экраны разной плотности пикселей, но это не требовалось
    -->
    <img class="preview__img" src="@/assets/img/img.png" alt="Превью">
    <div class="preview__info">
      <Sekeleton :lines="1" height="26px" radius="8px" />
      <div class='preview__descr'>
        <Sekeleton :lines="1" max-width="155px" height="10px" radius="4px" />
        <Sekeleton :lines="1" max-width="190px" height="10px" radius="4px" />
        <Sekeleton :lines="1" max-width="170px" height="10px" radius="4px" />
        <Sekeleton :lines="1" max-width="160px" height="10px" radius="4px" />
        <Sekeleton :lines="1" max-width="140px" height="10px" radius="4px" />
      </div>
      <Sekeleton :lines="1" max-width="80px" height="10px" radius="4px" />
    </div>
  </Card>
</template>

<style lang="scss" scoped>
.preview {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 18px 0 24px 0;

  &__img {
    width: 100%;
    border-radius: 8px;
    padding: 0 14px;
  }

  &__info {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 24px;
    padding: 0 23px;
    min-height: 198px;
  }

  &__descr {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    gap: 16px;
  }

}
</style>
