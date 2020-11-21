<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <img src="./src/assets/user_default.PNG" alt="Default User Image">
      <h1 class="user-profile__username"> @{{user.username}} </h1>
      <div class="user-profile__follower-count">
        <strong>Followers:</strong> {{ followers }}
      </div>
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '@_TehseenSajjad',
        firstName: 'Tehseen',
        lastName: 'Sajjad',
        email: 'tehseenyoung@gmail.com',
        isAdmin: true
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

.user-profile__follower-count {
  padding: 20px;
}

h1 {
  margin: 0;
}
</style>