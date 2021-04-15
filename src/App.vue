<template>
  <div id="app">
    <h1>Search Git account</h1>
    <input type="text" class="form-control" v-model="search" >
    <button class="form-control" @click="onSearch">Search</button>
    <Users :username="username"></Users>
    <router-view />
  </div>
</template>

<script>
  import Users from '@/components/Users.vue'
  export default({
    name:"app",
    data(){
      return{
        search:null,
        username:null
      }
    },
    methods:{
      onSearch(){
        this.username = this.search
        this.search = null
      }
    },
    components:{
      Users
    },
  })
</script>