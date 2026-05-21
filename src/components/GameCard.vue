<template>
  <div
    class="card"
    :class="{
      opened: card.opened,
      removed: card.removed
    }"
    @click="flip"
  >
    <div v-if="!card.opened">
      ?
    </div>

    <div v-if="card.opened">
      {{ card.value }}
    </div>

    <div class="card__layer">
      Слой {{ card.layer }}
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  props: {
    card: Object
  },

  methods: {
    ...mapActions(['flipCard']),

    flip() {
      this.flipCard(this.card.id)
    }
  }
}
</script>

<style scoped lang="scss">
.card {
  height: 120px;
  background: white;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  font-size: 32px;
  position: relative;
  border: 2px solid purple;

  &.opened {
    background: #dfb8ff;
  }

  &.removed {
    opacity: 0;
    pointer-events: none;
  }

  &__layer {
    position: absolute;
    bottom: 5px;
    right: 5px;
    font-size: 12px;
  }
}
</style>