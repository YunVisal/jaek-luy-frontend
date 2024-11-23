<template>
  <div class="w-full p-2 text-lg border border-black rounded-lg flex items-center space-x-2">
    <input id="password" class="flex-1 outline-none" :type="inputType" name="password" placeholder="*******"
      :value="modelValue" @input="updateValue($event.target?.value)" />
    <button type="button" class="w-[1.5rem] h-[1.5rem]" @click="toggleShowPassword">
      <VisibilityIcon v-if="!isShownPassword" />
      <VisibilityOffIcon v-else />
    </button>
  </div>
</template>

<script lang="ts" setup>
import { computed, defineProps, ref } from 'vue';
import VisibilityIcon from '../icon/VisibilityIcon.vue';
import VisibilityOffIcon from '../icon/VisibilityOffIcon.vue';

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

const isShownPassword = ref(false);
const toggleShowPassword = () => {
  isShownPassword.value = !isShownPassword.value;
}

const inputType = computed(() => isShownPassword.value ? 'text' : 'password')
</script>
