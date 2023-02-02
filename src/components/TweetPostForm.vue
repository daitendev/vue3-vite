<script setup lang="ts">
import { ref, defineEmits } from 'vue'
const inputtingDescription = ref<string>('')

const emit = defineEmits(['post-tweet'])
const postTweet = () => {
  emit('post-tweet', inputtingDescription.value)
}
</script>

<template>
  <div class="form-container">
    <input v-model="inputtingDescription" />
    <button @click="postTweet">post</button>
  </div>
</template>

<style scoped>

</style>