<template>
  <div class="default-header">
    <div class="container">
      <div class="default-header__content" @click="scrollToTop">
        Rick and Morty APP
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DefaultHeader',
  methods: {
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth',
      })
    },
  },
}
</script>

<style lang="scss">
.default-header {
  background-color: $grey;
  position: sticky;
  top: 0;
  z-index: 100;

  &__content {
    display: inline-block;
    padding: 7px 0;
    font-size: 12px;
    line-height: 14px;
    font-weight: 500;
    cursor: pointer;

    @media (min-width: $mq-tablet) {
      padding: 14px 0;
      font-size: 22px;
      line-height: 26px;
    }

    @media (min-width: $mq-laptop) {
      padding: 16px 0;
      font-size: 26px;
      line-height: 30px;
    }

    @media (min-width: $mq-desktop) {
      padding: 18px 0;
      font-size: 30px;
      line-height: 35px;
    }
  }
}
</style>
