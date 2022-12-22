<template>
  <div
    class="buy-btn-container is-flex"
    :class="{ 'container-transition': isOpen }">
    <NeoButton
      :label="label"
      :variant="varient"
      :class="{ 'is-left button-transition': isOpen }"
      class="is-right min-width"
      @click.native="onClick" />
    <div v-show="!isOpen">
      <slot name="placholder">
        <div class="placeholder" />
      </slot>
    </div>

    <div
      v-show="isOpen"
      class="is-align-items-center text-transition"
      :class="{ 'is-flex': isOpen }">
      <slot />
    </div>
  </div>
</template>

<script lang="ts" setup>
import NeoButton from '../NeoButton/NeoButton.vue'
import { LocaleMessage } from 'vue-i18n'

export interface Props {
  primaryLabel: string | LocaleMessage
  secondaryLabel: string | LocaleMessage | string[] | LocaleMessage[]
  varient?: 'default' | 'primary' | 'secondary'
  events: string[]
}
const props = withDefaults(defineProps<Props>(), {
  varient: 'primary',
})
const clickCounter = ref(0)

const emit = defineEmits(['click'])
const isOpen = ref(false)

const label = computed(() => {
  if (!isOpen.value) {
    return props.primaryLabel
  }
  if (Array.isArray(props.secondaryLabel)) {
    return props.secondaryLabel[clickCounter.value - 1]
  }
  return props.secondaryLabel
})

const onClick = () => {
  emit('click', props.events[clickCounter.value])
  clickCounter.value++

  if (clickCounter.value == 1) {
    isOpen.value = true
  }
  if (clickCounter.value == props.events.length) {
    isOpen.value = false
    clickCounter.value = 0
  }
}
</script>

<style lang="scss">
@import './NeoSlidingButton.scss';
.placeholder {
  min-width: 275px;
}
</style>
