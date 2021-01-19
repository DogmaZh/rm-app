<template>
  <div class="character-list-item" @click="$emit('toDetail', item.id)">
    <div class="character-list-item__content">
      <img class="character-list-item__image" :src="item.image" />
      <div class="character-list-item__name">{{ item.name }}</div>
    </div>
    <div class="character-list-item__background">To character >></div>
  </div>
</template>

<script>
export default {
  name: 'CharacterListItem',
  props: {
    item: {
      type: Object,
      default: () => {},
    },
  },
}
</script>

<style lang="scss">
.character-list-item {
  border-radius: 5px;
  width: 100%;
  cursor: pointer;
  position: relative;

  &:hover {
    box-shadow: 3px 6px 10px rgba(0, 0, 0, 0.2);
    transition: 0.4s;

    @media (min-width: $mq-laptop) {
      .character-list-item__content {
        top: 25px;
        left: 15px;
        transition: 0.4s;
      }
    }
  }

  &__content {
    border: 1px solid #000000;
    position: relative;
    display: flex;
    z-index: 10;
    border-radius: 5px;
    background-color: $white;
    width: 100%;
    top: 0;
    left: 0;
    transition: top 0.4s, left 0.4s;
  }

  &__image {
    width: 50px;
    height: 50px;
    border-radius: 5px;

    @media (min-width: $mq-tablet) {
      width: 75px;
      height: 75px;
    }

    @media (min-width: $mq-laptop) {
      width: 100px;
      height: 100px;
    }

    @media (min-width: $mq-desktop) {
      width: 125px;
      height: 125px;
    }
  }

  &__name {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;

    font-size: 12px;
    line-height: 14px;
    padding: 0 5px;

    @media (min-width: $mq-tablet) {
      font-size: 14px;
      line-height: 16px;
      padding: 0 10px;
    }

    @media (min-width: $mq-laptop) {
      font-size: 16px;
      line-height: 19px;
    }

    @media (min-width: $mq-desktop) {
      font-size: 18px;
      line-height: 21px;
    }
  }

  &__background {
    display: none;
    z-index: 1;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    border-radius: 5px;
    padding: 5px 10px;
    background-color: #24325fff;
    color: $white;

    @media (min-width: $mq-laptop) {
      display: block;
    }
  }
}
</style>
