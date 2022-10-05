<template>
  <div class="">
    <h1>{{text}}</h1>
    <button @click="isShow = !isShow">html on/off</button>
    <!-- 동적 컴포넌트 -->
    <Dynamic />
    <!-- 동영상 -->
    <Video />
    <!-- 컨텐츠 내 태그 처리 -->
    <Html v-if="isShow" />
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const text = '메인이다';
    const isShow = ref(false);

    return { text, isShow }
  }
}
</script>