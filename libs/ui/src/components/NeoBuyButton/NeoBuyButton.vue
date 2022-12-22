<template>
  <div
    class="buy-btn-container is-flex"
    :class="{ 'container-transition': isOpen }">
    <NeoButton
      :label="btnLabel"
      variant="primary"
      :class="{ 'float-left button-transition': isOpen }"
      class="float-right"
      @click.native="toggle" />
    <div
      v-show="isOpen"
      class="px-4 is-align-items-center text-transition"
      :class="{ 'is-flex': isOpen }">
      Buy Nft on RMRK
    </div>
  </div>
</template>

<script lang="ts" setup>
import NeoButton from '../NeoButton/NeoButton.vue'
const emit = defineEmits(['click'])
const isOpen = ref(false)
const btnLabel = ref('Buy')
const toggle = () => {
  const willOpen = !isOpen.value
  isOpen.value = willOpen
  btnLabel.value = willOpen ? 'Confirm' : 'Buy'
  emit('click', willOpen ? 'open' : 'close')
}
</script>

<style lang="scss">
@import './NeoBuyButton.scss';
</style>
