<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'

type Tweet = {
  id: number,
  description: string
}
type Props = {
  tweets: Tweet[]
}

defineProps<Props>()

const emit = defineEmits(['delete-tweet'])

const deleteTweet = (id: number) => {
  emit('delete-tweet', id)
}

</script>

<template>
  <div class="tweet-container">
    <ul>
      <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
        <span>
          {{ tweet.description }}
        </span>
        <button @click="deleteTweet(tweet.id)">delete</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>