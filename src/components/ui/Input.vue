<template>
  <label>
    {{ label }}
    <input
      :type="type"
      :placeholder="placeholder"
      :value="localValue"
      @input="inputHandler"
      :class="{'error': error}"
    >
    <p v-if="error" class="error-message">{{ error }}</p>
  </label>
</template>

<script setup lang="ts">
import { ref, toRefs } from 'vue';

const props = defineProps({
  type: {
    type: String,
    default: 'text'
  },
  placeholder: {
    type: String,
    default: ''
  },
  modelValue: {
    type: [String, Number],
    default: ''
  },
  label: {
    type: String,
    default: ''
  },
  error: {
    type: String,
  },
});

const emit = defineEmits(['update:modelValue']);

const { modelValue } = toRefs(props);
const localValue = ref(modelValue.value);

const inputHandler = (event: Event) => {
  const target = event.target as HTMLInputElement;
  localValue.value = target.value;
  emit('update:modelValue', target.value);
};
</script>

<style scoped lang="scss">
label {
  display: block;
  margin-bottom: 10px;

  & > input {
    width: 100%;
    padding: 10px 15px;
    border-radius: 5px;
    border: solid 1px #ccc;
    background-color: #fff;
    margin-top: 5px;
    
    &.error {
      border: solid 1px #ff0707;
    }
  }
}

.error-message {
  font-size: 12px;
  color: #ff0707
}
</style>