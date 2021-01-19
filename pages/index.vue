<template>
  <div class="index-page">
    <div class="container">
      <template v-if="info">
        <InfinityScrollList
          :loading="loading"
          :trigger-offset="25"
          @getMore="loadMore"
        >
          <CharacterListItem
            v-for="character in charactersList"
            :key="character.id"
            :item="character"
            @toDetail="
              $router.push({ name: 'characters-id', params: { id: $event } })
            "
          />
        </InfinityScrollList>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $http }) {
    const { results, info } = await $http.$get(
      'https://rickandmortyapi.com/api/character'
    )
    return { charactersList: results, info }
  },
  data() {
    return {
      page: 1,
      loading: false,
    }
  },
  methods: {
    async loadMore() {
      this.loading = true
      const { results, info } = await this.$http.$get(this.info.next)
      this.charactersList = [...this.charactersList, ...results]
      this.info = info
      this.loading = false
    },
  },
}
</script>

<style lang="scss">
.index-page {
  height: 100%;
  padding-top: 11px;

  @media (min-width: $mq-tablet) {
    padding-top: 20px;
  }

  @media (min-width: $mq-laptop) {
    padding-top: 30px;
  }

  @media (min-width: $mq-desktop) {
    padding-top: 40px;
  }
}
</style>
