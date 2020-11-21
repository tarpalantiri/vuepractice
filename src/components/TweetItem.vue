<template>
  <div class="tweet-item">
    <div class="user-profile__tweet">
      <div class="tweet-item__user">
          @{{ username }}
      </div>
      <div class="tweet-item__content">
        {{ tweet.content }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TweetItem",
  props: {
    username: {
      type: String,
      required: true
    },
    tweet: {
      type: Object,
      required: true,
    }
  }
};
</script>

<style>
.tweet-item {
  padding: 20px;

}
</style>