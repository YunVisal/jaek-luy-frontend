<script setup lang="ts">
import SignUpForm from './SignUpForm.vue';
</script>

<template>
  <article class="w-3/4 h-screen m-auto grid grid-cols-2">
    <section>
      <img class="w-1/2 h-full m-auto" src="../../assets/logo.svg" />
    </section>
    <section class="w-full h-3/4 m-auto">
      <SignUpForm />
    </section>
  </article>
</template>
