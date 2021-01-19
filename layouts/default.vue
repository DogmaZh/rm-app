<template>
  <div class="default-layout">
    <DefaultHeader />
    <div class="default-layout__content">
      <Nuxt />
    </div>
    <!-- <DefaultFooter /> -->
  </div>
</template>

<style lang="scss">
.default-layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;

  &__content {
    width: 100%;
    height: 100%;
    margin: 0 auto;
  }
}
</style>
