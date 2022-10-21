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
      <n-button type="info" round ghost @click="gen16"> 16 x 16 </n-button>
      <n-button type="info" round ghost @click="gen32"> 32 x 32 </n-button>
      <n-button type="info" round ghost @click="gen64"> 64 x 64 </n-button>
      <n-button type="info" round ghost @click="gen128"> 128 x 128 </n-button>
      <n-button type="info" round ghost @click="gen256"> 256 x 256 </n-button>
      <n-button type="info" round ghost @click="gen512"> 512 x 512 </n-button>
    </div>

    <div class="genview" v-if="src">
      <n-image :width="iwidth" :height="iheight" :src="imgblobview" />
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
const iwidth = ref(128)
const iheight = ref(128)
const aupload = (e: any) => {
  src.value = window.URL.createObjectURL(e.file.file)
}
const imgblobview = computed(() => {
  return src.value
})
const gen16 = () => {
  iwidth.value = 16
  iheight.value = 16
}
const gen32 = () => {
  iwidth.value = 32
  iheight.value = 32
}
const gen64 = () => {
  iwidth.value = 64
  iheight.value = 64
}
const gen128 = () => {
  iwidth.value = 128
  iheight.value = 128
}
const gen256 = () => {
  iwidth.value = 256
  iheight.value = 256
}
const gen512 = () => {
  iwidth.value = 512
  iheight.value = 512
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
  flex-direction: column;
  align-items: center;
  flex-wrap: no-wrap;
  height: 100vh;
  justify-content: space-around;
  overflow: scroll;
}
.genclick {
  display: flex;
  flex-wrap: wrap;
}
.footer {
  text-align: center;
  position: fixed;
  top: 100%;
  transform: translateY(-100%);
  width: 100vw;
}
</style>
