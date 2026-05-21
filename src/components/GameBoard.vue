<template>
  <div class="board-wrapper">
    <div class="board">
      <GameCard
        v-for="card in currentLayerCards"
        :key="card.id"
        :card="card"
      />
    </div>

    <div class="board__info">
      Слой {{ currentLayer }} из {{ layers }}
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import GameCard from './GameCard.vue'

export default {
  components: {
    GameCard
  },

  computed: {
    ...mapGetters([
      'cards',
      'currentLayer',
      'layers'
    ]),

    currentLayerCards() {
      return this.cards.filter(
        card =>
          card.layer === this.currentLayer &&
          !card.removed
      )
    }
  }
}
</script>

<style scoped lang="scss">
.board-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.board {
  display: grid;
  grid-template-columns: repeat(4, 120px);
  gap: 12px;
  justify-content: center;
}

.board__info {
  font-size: 24px;
  font-weight: bold;
}
</style>