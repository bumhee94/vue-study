<template>
  <div :class="text">
    <h2>{{text}}</h2>
  </div>
</template>

<script>
export default {
  name: 'Params',
  props:{
    propsKey: String
  },
  setup(props) {
    const text = props.propsKey;

    return { text }
  }
}
</script>