<template>
  <div class="default-footer">
    <div class="container">
      <div class="default-footer__content">
        &copy; {{ curYear }} Rick and Morty APP
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DefaultFooter',
  computed: {
    curYear() {
      return new Date().getFullYear()
    },
  },
}
</script>

<style lang="scss">
.default-footer {
  margin-top: auto;

  &__content {
    padding: 12px 0;
  }
}
</style>
