<script setup>
import { defineEmits } from 'vue'
// 通知父組件修改圖片色彩控制值
const emits = defineEmits(['selectOption'])

const selectOption = (isColor) => {
    emits('selectOption', isColor)
}
</script>

<template>
    <!-- 左側導航區 -->
    <!-- expand-on-hover 游標摸到導航時展開抽屜-->
    <!-- rail 控制抽屜開、閉-->
    <v-navigation-drawer expand-on-hover rail>
        <v-list>
            <!-- 人像組件 -->
            <v-list-item prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
                subtitle="sandra_a88@gmailcom" title="Chou Adams"></v-list-item>
        </v-list>

        <!-- 分隔線組件 -->
        <v-divider />

        <v-list density="compact" nav>
            <!-- 彩色圖導航 -->
            <v-list-item prepend-icon="mdi-image" title="Color Gallery" value="color" @click="selectOption(true)" />
            <!-- 灰階圖導航 -->
            <v-list-item prepend-icon="mdi-dialpad" title="GreySpace Gallery" value="color"
                @click="selectOption(false)" />
        </v-list>
    </v-navigation-drawer>
</template>