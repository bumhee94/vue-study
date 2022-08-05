<template>
  <div class="">{{text}}
    <A />
    <B />
    <C />
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