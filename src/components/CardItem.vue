<template>
  <div class="card">
    <div class="card-back" v-show="!card.isShow" @click="handleClickCard(card)">
      <img src="../assets/img/card-backside.png" alt="" />
    </div>
    <div class="card-front" v-show="card.isShow">
      <img :src="require(`../assets/img/${card.img}`)" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardItem',
  props: {
    card: {
      type: Object
    }
  },
  setup (props, ctx) {
    const handleClickCard = (card) => {
      //   card.isShow = true
      ctx.emit('onClickCard', card)
    }

    return {
      handleClickCard
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  position: relative;
  &-back {
    cursor: pointer;
  }
  &-back,
  &-front {
    img {
      display: block;
      width: 100%;
      object-fit: cover;
    }
  }
}
</style>