<template>
  <div class="dynamic">
    <h2>동적 컴포넌트</h2>
    <!-- 배열식 동적 컴포넌트 -->
    <NuxtDynamic v-for="component in components" :name="component" some-property="some-value" />
    <!-- 단일 동적 컴포넌트 -->
    <NuxtDynamic :name="componentName" props-key="value" />
  </div>
</template>

<script>
export default {
  setup() {
    setTimeout(() => {

    }, 1000)
    const components = ['A', 'Params']; // DB 컴포넌트
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