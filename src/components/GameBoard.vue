<template>
  <div class="board">
    <GameCard
      v-for="card in cards"
      :key="card.id"
      :card="card"
    />
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
    ...mapGetters(['cards'])
  }
}
</script>

<style scoped lang="scss">
.board {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 10px;
  margin-top: 20px;
}
</style>