<template>
  <input :id="name" class="w-full p-2 text-lg border border-black outline-none rounded-lg" :name="name"
    :placeholder="props.placeholder" :value="modelValue" @input="updateValue($event.target?.value)" v-bind="$attrs" />
</template>

<script lang="ts" setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  name: {
    type: String,
    required: true
  },
  placeholder: {
    type: String,
    required: true
  },
  modelValue: {
    type: String,
    required: true
  }
});

const emit = defineEmits(['update:modelValue']);
const updateValue = (value: string) => {
  emit('update:modelValue', value)
}
</script>
