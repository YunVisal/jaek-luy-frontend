<template>
  <form class="space-y-5" v-on:submit.prevent="signUp">
    <h1 class="text-3xl">Introduce yourself</h1>
    <div class="space-y-3">
      <div>
        <label for="username" class="block text-xl">My name is:</label>
        <TextInput type="text" name="username" placeholder="John Doe" v-model="form.userName" />
      </div>
      <div class="space-y-1" v-if="isNameInputed">
        <label for="email" class="block text-xl">Here's my email:</label>
        <TextInput type="email" name="email" placeholder="user@example.com" v-model="form.email" />
      </div>
      <div v-if="isNameInputed">
        <label for="password" class="block text-xl">And here's my password:</label>
        <PasswordInput name="password" placeholder="*******" v-model="form.password" />
      </div>
      <div class="w-3/4 flex items-center space-x-2">
        <button class="p-3 text-xl bg-[#ccc] rounded-lg">Sign me up!</button>
        <p>or</p>
        <button class="p-1 text-md bg-[#ccc] rounded-md">Sign up with Google</button>
      </div>
    </div>
  </form>
</template>

<script lang="ts">
import { reactive, ref, watch } from 'vue';
import TextInput from '../reusable/TextInput.vue';
import PasswordInput from '../reusable/PasswordInput.vue';

export default {
  name: "SignUpForm",
  components: {
    TextInput,
    PasswordInput
  },
  setup() {
    const form = reactive({
      userName: '',
      email: '',
      password: ''
    });

    const isNameInputed = ref(false);
    watch(() => form.userName, (newValue, oldValue) => {
      if (!isNameInputed.value && !oldValue && newValue) {
        isNameInputed.value = true;
      }
    })

    const signUp = () => {
      console.log(form);
    }

    return {
      form,
      isNameInputed,
      signUp
    };
  }
}
</script>
