<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <Navbar/>
    <AllFriends :friends="friends" @delete="deleteFriend" />
    <OnlineFriends :friends="friends" />
  </div>
</template>

<script>
import Navbar from './Navbar'
import AllFriends from './AllFriends'
import OnlineFriends from './OnlineFriends'
export default {
  name: 'app',
  components: {
    Navbar,
    OnlineFriends,
    AllFriends
  },
  data () {
    return {
      title: ' My First Vue App',
      friends: [
        { name: 'Mario', online: true },
        { name: 'Luigi', online: false },
        { name: 'Toad', online: true },
        { name: 'Browser', online: false }
      ]
    }
  },
    methods: {
      //typically called payload. Doesn't have to be named that. Just a common convention
      deleteFriend(payload) {
        console.log(payload)
        this.friends = this.friends.filter(friend => {
          return friend.name !== payload.name
        })
      }
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1{
  font-weight: normal;
  color: #444;
  text-align: center;
}
</style>
