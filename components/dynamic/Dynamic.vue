<template>
  <div class="dynamic">
    <h2>동적 컴포넌트</h2>
    <!-- 배열식 동적 컴포넌트 -->
    <NuxtDynamic v-for="component in components" :name="component" some-property="some-value" />
    <!-- 단일 동적 컴포넌트 -->
    <NuxtDynamic :name="componentName" some-property="some-value" />
  </div>
</template>

<script>
export default {
  setup() {
    const components = ['A','B','C'];
    let componentName = null;
    const chgComponent = () => {
      let temp = components[Math.floor(Math.random() * components.length)];
      console.log(temp);
      componentName = temp;
    }
    chgComponent();

    return { components, componentName, chgComponent }
  }
}
</script>