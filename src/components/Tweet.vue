<script setup lang="ts">
import { ref, reactive } from 'vue'
const tweets = ref(
  [
    { id: 0, description: 'Hello' },
    { id: 1, description: 'two' },
    { id: 2, description: 'three' },
  ]
)
const inputtingDescription = ref<string>('')

const postTweet = () => {
  const tweet = { id: Math.random(), description: inputtingDescription.value }
  inputtingDescription.value = ''
  tweets.value.push(tweet)
}
const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(tweet => tweet.id !== id)
}
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <div class="form-container">
      <input v-model="inputtingDescription" />
      <button @click="postTweet">post</button>
    </div>
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
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tweet-list {
  list-style: none;
}
</style>