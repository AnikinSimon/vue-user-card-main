<template>
  <div id="app">
    <UserCard :avatar="avatar" :firstname="firstName" :lastname="lastName" 
    :nickname="nickname" :adress="adress" :phone="phone" :email="email"/>
    <button v-on:click="getUserData">Обновить</button>
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
        avatar: '',
        login: '',
        firstName: '',
        lastName: '',
        adress: '',
        phone: '',
        email: ''
      }
    },
    methods:{
      getUserData(){
        this.axios.get('https://randomuser.me/api/')
          .then((response)=>{
            console.clear()
            let info = response.data.results[0]
            console.log(info)
            this.adress = info.location.city + "," + info.location.street.name;
            this.avatar = info.picture.medium;
            this.nickname = info.login.username;
            this.email = info.email;
            this.phone = info.phone;
            this.firstName = info.name.first;
            this.lastName = info.name.last;
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
  }
</style>
