<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <UserCard :avatar="avatar" :firstname="firstname" :lastname="lastname" 
    :nickname="nickname" :adress="adress" :phone="phone" :email="email"/>
  </div>
</template>

<script>
  import UserCard from "./components/UserCard.vue"
  export default {
    name: 'App',
    components: {
      UserCard
    },
    data() {
        return {
            avatar: 'https://pixelbox.ru/wp-content/uploads/2021/05/ava-vk-animal-91.jpg',
            firstname: "Иванов Иван",
            lastname: "Иванович",
            nickname: "romashka",
            adress: "Москва, Юбилейная 50",
            phone: "+7-495-266-57-34",
            email: "coldrabbit48@example.com"
        }
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
