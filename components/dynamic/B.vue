<template>
  <div :class="text">
    <h2>{{text}}</h2>
  </div>
</template>

<script>
export default {
  name: 'B',
  setup() {
    const text = 'B';

    return { text }
  }
}
</script>