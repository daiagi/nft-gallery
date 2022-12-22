<template>
  <o-button
    :class="{ 'is-neo': true, active: active, [variant]: true }"
    :size="size"
    :icon-right="icon"
    icon-pack="fas">
    {{ label }}
  </o-button>
</template>

<script lang="ts" setup>
import { OButton } from '@oruga-ui/oruga'

const props = defineProps<{
  size?: string
  icon?: string
  label?: string
  active?: boolean
  variant?: 'default' | 'primary' | 'secondary'
}>()

const variant = computed(() => props.variant || 'default')
</script>

<style lang="scss" scoped>
@import '@oruga-ui/oruga/dist/oruga-full-vars.min.css';
@import '../../scss/variable.scss';
.is-neo {
  border-radius: 0;
  color: hsl(0deg, 0%, 4%);
  background: hsl(0deg, 0%, 100%);
  border: 1px solid hsl(0deg, 0%, 4%);
  -webkit-box-shadow: 4px 4px hsl(0deg, 0%, 4%);
  box-shadow: 4px 4px hsl(0deg, 0%, 4%);
  font-family: inherit;
  padding-top: 8px;
  padding-bottom: 8px;

  &:hover {
    background: #ffe5f3;
  }

  &.active {
    color: hsl(0deg, 0%, 100%);
    background-color: hsl(0deg, 0%, 4%);
  }

  &.primary {
    background: #ff7ac3;

    &:hover {
      background: white;
    }
  }

  &.secondary {
    background: #6188e7;

    &:hover {
      background: white;
    }
  }
}

.dark-mode .is-neo {
  color: hsl(0deg, 0%, 100%);
  background: hsl(330, 4%, 9%);
  border: 1px solid hsl(0deg, 0%, 100%);
  -webkit-box-shadow: 4px 4px hsl(0deg, 0%, 100%);
  box-shadow: 4px 4px hsl(0deg, 0%, 100%);

  &:hover {
    background: #ff7ac3;
    color: hsl(0deg, 0%, 4%);
  }
  &.active {
    color: hsl(0deg, 0%, 4%);
    background-color: hsl(0deg, 0%, 100%);
  }

  &.primary {
    background: #ff7ac3;
    color: black;

    &:hover {
      background: hsl(330, 4%, 9%);
      color: hsl(0deg, 0%, 100%);
    }
  }

  &.secondary {
    background: #6188e7;
    color: black;

    &:hover {
      background: hsl(330, 4%, 9%);
      color: hsl(0deg, 0%, 100%);
    }
  }
}
</style>
