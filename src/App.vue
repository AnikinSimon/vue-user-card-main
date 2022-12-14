<template>
  <div id="app">
    <button v-on:click="getUserData">Обновить</button>
    <UserCard v-for="(user, index) in users" v-bind:key="index" :avatar="user.avatar" :firstname="user.firstName" :lastname="user.lastName" 
    :nickname="user.nickname" :adress="user.adress" :phone="user.phone" :email="user.email"/>
  </div>
</template>

<script>
  import UserCard from "./components/UserCard.vue"
  export default {
    name: 'App',
    components: {
      UserCard
    },
    data(){
      return {
        users: []
      }
    },
    methods:{
      getUserData(){
        this.axios.get('https://randomuser.me/api/')
          .then((response)=>{
            let info = response.data.results[0]
            if (this.users.length == 10) {
              this.users.pop()
            }
            this.users.unshift({
                "adress": info.location.city + "," + info.location.street.name,
                "avatar": info.picture.medium,
                "nickname": info.login.username,
                "email":info.email,
                "phone": info.phone,
                "firstName": info.name.first,
                "lastName": info.name.last
            })
          })
      }
    },
    mounted(){
      this.getUserData();
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    display: flex;
    flex-wrap: wrap;
  }
</style>
