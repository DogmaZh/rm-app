<template>
  <div class="infinity-scroll-list">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'InfinityScrollList',
  props: {
    loading: {
      type: Boolean,
      default: false,
    },
    triggerOffset: {
      type: Number,
      default: 100,
    },
  },
  data() {
    return {
      scrolledToBottom: false,
    }
  },
  watch: {
    scrolledToBottom() {
      if (!this.loading) {
        this.$emit('getMore')
      }
    },
  },
  mounted() {
    this.scrolledToBottom = this.isBottomOfWindow()
    this.scroll()
  },
  methods: {
    isBottomOfWindow() {
      return (
        Math.max(
          window.pageYOffset,
          document.documentElement.scrollTop,
          document.body.scrollTop
        ) +
          this.triggerOffset +
          window.innerHeight >=
        document.documentElement.offsetHeight
      )
    },
    scroll() {
      window.onscroll = () => {
        if (this.isBottomOfWindow()) {
          this.scrolledToBottom = true
        } else {
          this.scrolledToBottom = false
        }
      }
    },
  },
}
</script>

<style lang="scss">
.infinity-scroll-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-row-gap: 16px;
  grid-column-gap: 16px;
  margin-bottom: 50px;

  @media (min-width: $mq-tablet) {
    grid-template-columns: repeat(3, 1fr);
    grid-row-gap: 20px;
    grid-column-gap: 36px;
  }

  @media (min-width: $mq-laptop) {
    grid-template-columns: repeat(5, 1fr);
    grid-row-gap: 30px;
    grid-column-gap: 31px;
    margin-bottom: 100px;
  }

  @media (min-width: $mq-desktop) {
    grid-row-gap: 40px;
    grid-column-gap: 69px;
  }
}
</style>
