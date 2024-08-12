<script setup>
import SideBar from './components/SideBar.vue'
import ImageGallery from './components/ImageGallery.vue'
import { ref } from 'vue'

// 畫廊圖片展區 保存黑白色或彩色 色彩控制值
const isWithColor = ref(true)
const onSelectOption = (isColor) => {
  isWithColor.value = isColor
}

</script>

<template>
  <v-app>
    <!-- SideBar -->
    <!-- 子組件SideBar傳值+通知父組件App切換圖片顏色所用的控制值 -->
    <SideBar @selectOption="onSelectOption" />
    <v-main>
      <!-- cards -->
      <!-- 父組件App傳遞控制值交給子組件ImageGallery 以選擇取得彩色圖片或灰階圖片-->
      <ImageGallery :isWithColor="isWithColor" />
    </v-main>
  </v-app>
</template>
