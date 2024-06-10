<template>
  <button
    :class="`button button__${variant}`"
    @click="onClick"
  >
    <slot />
  </button>
</template>

<script setup lang="ts">
import { toRefs } from 'vue';

type VariantType = 'primary' | 'secondary' | 'transparent';

const props = defineProps<{
  variant?: VariantType;
}>();

const emit = defineEmits<{
  (e: 'click'): void;
}>();

const { variant } = toRefs(props);

const onClick = () => {
  emit('click');
};
</script>

