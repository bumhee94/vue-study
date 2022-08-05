<template>
  <div class="">
    <h1>{{text}}</h1>
    <!-- 동적 컴포넌트 -->
    <Dynamic />
    <!-- 컨텐츠 내 태그 처리 -->
    <Html />
  </div>
</template>

<script>
export default {
  setup() {
    const text = '메인이다';

    return { text }
  }
}
</script>