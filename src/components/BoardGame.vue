<template>
  <div class="board-game">
    <h1>Mini Game Flip Card</h1>
    <button @click="restartGame">Restart Game</button>
    <p>Matched: {{ statusMatched }}</p>
    <p>Remaining: {{ statusRemaining }}</p>
    <div class="list-card">
      <CardItem
        v-for="card in listCard"
        :key="card.id"
        :card="card"
        @onClickCard="handleOnClickCard"
      />
    </div>
  </div>
</template>

<script>
import CardItem from './CardItem.vue'
import { ref, reactive, computed } from 'vue'

export default {
  name: 'BoardGame',
  components: {
    CardItem
  },
  setup () {
    const listCard = reactive([
      {
        id: 1,
        img: '1.png',
        value: 1,
        isShow: false,
        isMatched: false
      },
      {
        id: 2,
        img: '2.png',
        value: 2,
        isShow: false,
        isMatched: false
      },
      {
        id: 3,
        img: '3.png',
        value: 3,
        isShow: false,
        isMatched: false
      },
      {
        id: 4,
        img: '4.png',
        value: 4,
        isShow: false,
        isMatched: false
      },
      {
        id: 5,
        img: '5.png',
        value: 5,
        isShow: false,
        isMatched: false
      },
      {
        id: 6,
        img: '6.png',
        value: 6,
        isShow: false,
        isMatched: false
      },
      {
        id: 7,
        img: '7.png',
        value: 7,
        isShow: false,
        isMatched: false
      },
      {
        id: 8,
        img: '8.png',
        value: 8,
        isShow: false,
        isMatched: false
      },
      {
        id: 9,
        img: '9.png',
        value: 9,
        isShow: false,
        isMatched: false
      },
      {
        id: 10,
        img: '10.png',
        value: 10,
        isShow: false,
        isMatched: false
      },
      {
        id: 11,
        img: '11.png',
        value: 11,
        isShow: false,
        isMatched: false
      },
      {
        id: 12,
        img: '12.png',
        value: 12,
        isShow: false,
        isMatched: false
      },
      {
        id: 13,
        img: '13.png',
        value: 13,
        isShow: false,
        isMatched: false
      },
      {
        id: 14,
        img: '14.png',
        value: 14,
        isShow: false,
        isMatched: false
      },
      {
        id: 15,
        img: '15.png',
        value: 15,
        isShow: false,
        isMatched: false
      },
      {
        id: 16,
        img: '16.png',
        value: 16,
        isShow: false,
        isMatched: false
      },
      {
        id: 17,
        img: '17.png',
        value: 17,
        isShow: false,
        isMatched: false
      },
      {
        id: 18,
        img: '18.png',
        value: 18,
        isShow: false,
        isMatched: false
      },
      {
        id: 19,
        img: '19.png',
        value: 19,
        isShow: false,
        isMatched: false
      },
      {
        id: 20,
        img: '20.png',
        value: 20,
        isShow: false,
        isMatched: false
      },
      {
        id: 21,
        img: '1.png',
        value: 1,
        isShow: false,
        isMatched: false
      },
      {
        id: 22,
        img: '2.png',
        value: 2,
        isShow: false,
        isMatched: false
      },
      {
        id: 23,
        img: '3.png',
        value: 3,
        isShow: false,
        isMatched: false
      },
      {
        id: 24,
        img: '4.png',
        value: 4,
        isShow: false,
        isMatched: false
      },
      {
        id: 25,
        img: '5.png',
        value: 5,
        isShow: false,
        isMatched: false
      },
      {
        id: 26,
        img: '6.png',
        value: 6,
        isShow: false,
        isMatched: false
      },
      {
        id: 27,
        img: '7.png',
        value: 7,
        isShow: false,
        isMatched: false
      },
      {
        id: 28,
        img: '8.png',
        value: 8,
        isShow: false,
        isMatched: false
      },
      {
        id: 29,
        img: '9.png',
        value: 9,
        isShow: false,
        isMatched: false
      },
      {
        id: 30,
        img: '10.png',
        value: 10,
        isShow: false,
        isMatched: false
      },
      {
        id: 31,
        img: '11.png',
        value: 11,
        isShow: false,
        isMatched: false
      },
      {
        id: 32,
        img: '12.png',
        value: 12,
        isShow: false,
        isMatched: false
      },
      {
        id: 33,
        img: '13.png',
        value: 13,
        isShow: false,
        isMatched: false
      },
      {
        id: 34,
        img: '14.png',
        value: 14,
        isShow: false,
        isMatched: false
      },
      {
        id: 35,
        img: '15.png',
        value: 15,
        isShow: false,
        isMatched: false
      },
      {
        id: 36,
        img: '16.png',
        value: 16,
        isShow: false,
        isMatched: false
      },
      {
        id: 37,
        img: '17.png',
        value: 17,
        isShow: false,
        isMatched: false
      },
      {
        id: 38,
        img: '18.png',
        value: 18,
        isShow: false,
        isMatched: false
      },
      {
        id: 39,
        img: '19.png',
        value: 19,
        isShow: false,
        isMatched: false
      },
      {
        id: 40,
        img: '20.png',
        value: 20,
        isShow: false,
        isMatched: false
      },
    ])
    const cardSelected = ref([])

    const handleOnClickCard = (card) => {
      // Show Card
      listCard.find(i => {
        if (i.id === card.id) {
          i.isShow = true
        }
      })

      // Card selected
      if (cardSelected.value[0] === undefined) {
        cardSelected.value[0] = card.value
      } else {
        cardSelected.value[1] = card.value
        checkMatched(cardSelected.value[0], cardSelected.value[1])
      }

      if (listCard.every(i => i.isMatched === true)) {
        alert('You Win!')
      }
    }

    // Rules
    function checkMatched (first, second) {
      if (first === second) {
        listCard.map(i => {
          if (i.value === first) {
            i.isMatched = true
          }
        })
      } else {
        listCard.map(i => {
          if (!i.isMatched) {
            setTimeout(() => {
              i.isShow = false
            }, 1000)
          }
        })
      }
      cardSelected.value = []
    }

    // Restart Game
    function restartGame () {
      listCard.sort(() => Math.random() - 0.5)
      listCard.map(i => (i.isMatched = false, i.isShow = false))
      cardSelected.value = []
    }
    restartGame()


    // Status 
    const statusMatched = computed(() => {
      return listCard.filter(i => i.isMatched).length / 2
    })

    const statusRemaining = computed(() => {
      return listCard.filter(i => !i.isMatched).length / 2
    })


    return {
      listCard,
      handleOnClickCard,
      cardSelected,
      statusMatched,
      statusRemaining,
      restartGame
    }
  }
}
</script>

<style lang="scss" scoped>
.list-card {
  padding: 32px 0;
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-gap: 24px;
}
</style>