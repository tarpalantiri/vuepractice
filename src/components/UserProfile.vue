<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__username"> @{{user.username}} </h1>
      <div class="user-profile__admin-badge" v-if="user.isAdmin">
        Admin
        </div>
      <div class="user-profile__follower-count">
        <strong>Followers:</strong> {{ followers }}
      </div>
    </div>
    <div class="user-profile__tweets-wrapper">
      <TweetItem
      v-for="tweet in user.tweets"
      :key="tweet.id"
      :username="user.username"
      :tweet="tweet"
      />
    </div>
  </div>
</template>

<script>
import TweetItem from 'src/components/TweetItem.vue';

export default {
  name: 'UserProfile',
  components: { TweetItem, },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '_TehseenSajjad',
        firstName: 'Tehseen',
        lastName: 'Sajjad',
        email: 'tehseenyoung@gmail.com',
        isAdmin: true,
        tweets: [
          { id: 1, content: "Tweet Content :)" },
          { id: 2, content: "Tweet Content # 2 :{}" }
        ]
      }
    }
  },

  watch: {
    followers(newFollowerCount, oldFollowerCount){
      if (oldFollowerCount < newFollowerCount) {
        alert(this.user.username + "has gained a follower");
      }
    }
  },

  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },

  methods: {
    followUser() {
      this.followers++;
    }
  },

  mounted() {
    this.followUser();
  }
}
</script>

<style>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #DFE2E8;
}

/* .user-profile__follower-count {
  padding: 20px;
} */

.user-profile__admin-badge {
  background: rebeccapurple;
  color: white;
  border-radius: 5px;
  border: 1px solid rebeccapurple;
  padding: 0px 15px;
  margin-right: auto;
  font-weight: bold;
}

div {
  margin: 2px;
}

img {
  height: 92px;
  width: 92px;
}

h1 {
  margin: 0;
}
</style>