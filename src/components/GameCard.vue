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
      <img
      :src="`/src/assets/cards/${card.value}.png`"
      class="card__image"
      />
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
  width: 120px;
  height: 120px;
  min-width: 120px;
  min-height: 120px;
  max-width: 120px;
  max-height: 120px;

  overflow: hidden;

  background: white;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  position: relative;
  border: 2px solid purple;

  &.opened {
    background: #dfb8ff;
  }

  &.removed {
    opacity: 0;
    pointer-events: none;
  }

  &__image {
    width: 80px;
    height: 80px;
    object-fit: contain;

    flex-shrink: 1;
  }

  &__layer {
    position: absolute;
    bottom: 5px;
    right: 5px;
    font-size: 12px;
  }
}
</style>