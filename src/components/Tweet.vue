<script setup lang="ts">
import TweetPostForm from './TweetPostForm.vue'
import TweetPostList from './TweetPostList.vue'
import { ref, reactive, defineProps } from 'vue'

const tweets = ref(
  [
    { id: 0, description: 'Hello' },
    { id: 1, description: 'two' },
    { id: 2, description: 'three' },
  ]
)
const postTweet = (description: string) => {
  const tweet = { id: Math.random(), description }
  tweets.value.push(tweet)
}
const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(tweet => tweet.id !== id)
}
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <TweetPostForm @post-tweet="postTweet" />
    <TweetPostList :tweets="tweets" @delete-tweet="deleteTweet" />
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