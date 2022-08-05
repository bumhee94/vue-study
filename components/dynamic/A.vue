<template>
  <div :class="text">
    <h2>{{text}}</h2>
  </div>
</template>

<script>
export default {
  name: 'A',
  setup() {
    const text = 'A';

    return { text }
  }
}
</script>