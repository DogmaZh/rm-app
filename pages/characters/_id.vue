<template>
  <div class="container">
    <div class="characters-details">
      <div class="characters-details__back" @click="$router.push('/')">
        Back to list
      </div>
      <div class="characters-details__title">{{ character.name }}</div>
      <div class="characters-details__about">
        <img class="characters-details__about-image" :src="character.image" />
        <div class="characters-details__about-info">
          <div class="characters-details__about-info-item">
            Gender: {{ character.gender }}
          </div>
          <div class="characters-details__about-info-item">
            Status: {{ character.status }}
          </div>
          <div class="characters-details__about-info-item">
            Location: {{ character.location.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $http }) {
    const result = await $http.$get(
      `https://rickandmortyapi.com/api/character/${params.id}`
    )
    return { character: result }
  },
}
</script>

<style lang="scss">
.characters-details {
  padding-top: 10px;

  &__back {
    display: inline-block;
    font-size: 12px;
    line-height: 14px;
    opacity: 0.5;
    text-decoration: underline;
    cursor: pointer;
    margin-bottom: 10px;

    &:hover {
      opacity: 1;
    }

    @media (min-width: $mq-tablet) {
      margin-bottom: 20px;
      font-size: 14px;
      line-height: 16px;
    }

    @media (min-width: $mq-laptop) {
      margin-bottom: 30px;
      font-size: 16px;
      line-height: 18px;
    }

    @media (min-width: $mq-desktop) {
      margin-bottom: 40px;
    }
  }

  &__title {
    text-align: center;
    font-size: 30px;
    line-height: 35px;
    margin-bottom: 20px;

    @media (min-width: $mq-tablet) {
      margin-bottom: 30px;
      font-size: 34px;
      line-height: 40px;
    }

    @media (min-width: $mq-laptop) {
      margin-bottom: 40px;
      font-size: 40px;
      line-height: 47px;
      text-align: left;
    }

    @media (min-width: $mq-desktop) {
      margin-bottom: 50px;
      font-size: 50px;
      line-height: 59px;
    }
  }

  &__about {
    display: flex;
    flex-direction: column;

    @media (min-width: $mq-tablet) {
      flex-direction: row;
    }
  }

  &__about-image {
    width: 150px;
    height: 150px;
    align-self: center;
    margin-bottom: 20px;

    @media (min-width: $mq-tablet) {
      width: 300px;
      height: 300px;
      margin-right: 40px;
      margin-bottom: 0;
    }

    @media (min-width: $mq-tablet) {
      margin-right: 50px;
    }
  }

  &__about-info {
    display: flex;
    flex-wrap: wrap;
    margin: -3px -5px;

    @media (min-width: $mq-tablet) {
      margin: 0;
      display: block;
    }
  }

  &__about-info-item {
    font-size: 14px;
    line-height: 16px;
    margin: 3px 5px;

    &:not(:last-child) {
      @media (min-width: $mq-tablet) {
        margin-bottom: 10px;
      }

      @media (min-width: $mq-laptop) {
        margin-bottom: 15px;
      }
    }

    @media (min-width: $mq-tablet) {
      margin: 0;
      font-size: 16px;
      line-height: 19px;
    }

    @media (min-width: $mq-laptop) {
      font-size: 24px;
      line-height: 28px;
    }

    @media (min-width: $mq-desktop) {
      font-size: 28px;
      line-height: 33px;
    }
  }
}
</style>
