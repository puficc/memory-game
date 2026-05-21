<template>
  <div class="game">
    <GameTimer />

    <div class="game__layer">
      Текущий слой: {{ currentLayer }}
    </div>

    <GameBoard />

    <FinishModal v-if="gameFinished" />
  </div>
</template>

<script>
import GameBoard from '../components/GameBoard.vue'
import GameTimer from '../components/GameTimer.vue'
import FinishModal from '../components/FinishModal.vue'

import { mapGetters } from 'vuex'

export default {
  components: {
    GameBoard,
    GameTimer,
    FinishModal
  },

  computed: {
    ...mapGetters([
      'gameFinished',
      'currentLayer'
    ])
  }
}
</script>

<style scoped lang="scss">
.game {
  min-height: 100vh;
  background: #f3f3f3;
  padding: 20px;
}
</style>