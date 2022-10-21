<template>
  <div class="header">
    <n-gradient-text type="info"> ICON Generator </n-gradient-text>
  </div>
  <div class="container">
    <div class="upload">
      <n-upload directory-dnd :max="1" accept=".png" :on-change="aupload">
        <n-upload-dragger>
          <div style="margin-bottom: 12px">
            <n-icon size="48" :depth="3">
              <archive-icon />
            </n-icon>
          </div>
          <n-text style="font-size: 16px">
            点击或者拖动png格式图片到该区域
          </n-text>
        </n-upload-dragger>
      </n-upload>
    </div>

    <div class="genclick" v-if="src">
      <n-button type="info" ghost @click="gen"> 生成 </n-button>
    </div>

    <div class="genview" v-if="src">
      <n-image width="300" :src="imgblobview" />
    </div>
  </div>
  <div class="footer">
    <n-card hoverable>
      <n-gradient-text :size="14" type="info">
        Created by baizhi958216 with Vue && Vite && Naive UI
      </n-gradient-text>
    </n-card>
  </div>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue'
import {
  NUpload,
  NUploadDragger,
  NIcon,
  NText,
  NButton,
  NGradientText,
  NImage,
  NCard,
} from 'naive-ui'
import { ArchiveOutline as ArchiveIcon } from '@vicons/ionicons5'
const src = ref('')
const aupload = (e: any) => {
  src.value = window.URL.createObjectURL(e.file.file)
}
const imgblobview = computed(() => {
  return src.value
})
const gen = () => {
  console.log(src.value)
}
</script>

<style scoped>
.header {
  font-size: 30px;
  user-select: none;
  text-align: center;
}
.container {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-wrap: wrap;
}
.footer {
  text-align: center;
  position: absolute;
  top: 100%;
  transform: translateY(-100%);
  width: 100vw;
}
</style>
