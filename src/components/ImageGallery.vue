<script setup>
import { defineProps } from 'vue'

// 接收父組件App傳遞圖片色彩控制值
const p = defineProps(["isWithColor"])

// 複製圖片網址到剪貼簿保存 stackoverflow
const copyURL = async (url) => {
    await navigator.clipboard.writeText(url)
}
</script>

<template>
    <!-- 卡片組件 -->
    <v-card class="mx-5 my-2 pa-3">
        <!-- vRow vCol 格線系統Grid system -->
        <v-row>
            <v-col v-for="(n) in 100" :key="n" cols="4" sm="3" lg="2">
                <v-hover
                    v-slot="{isHovering, props}"
                >
                    <v-card
                        :elevation="isHovering ? 12 : 2"
                        v-bind="props"
                        @click="copyURL(`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`)"
                    >
                        <v-img
                            :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`"
                            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`"
                            aspect-ratio="1" cover>
                            <template v-slot:placeholder>
                                <v-row align="center" class="fill-height ma-0" justify="center">
                                    <!-- 資源下載進度特效組件 -->
                                    <v-progress-circular color="grey-lighten-5" indeterminate />
                                </v-row>
                            </template>
                        </v-img>
                    </v-card>
                </v-hover>
            </v-col>
        </v-row>
    </v-card>
</template>