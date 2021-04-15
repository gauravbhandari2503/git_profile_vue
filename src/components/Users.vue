<template>
<div>
    <div class="card mt-5" style="width: 18rem;">
        <img class="card-img-top" :src="user.avatar_url" alt="Card image cap">
        <div class="card-body">
            <h5 class="card-title"><a href="`https://github.com/${username}`" target="_blank" >{{user.name}}</a></h5>
            <p class="card-text">Joined in: {{user.created_at}}</p>
            <p class="card-text">Bio: {{user.bio}}</p>
            <a href="#" class="btn btn-primary">{{user.followers}} Friends</a>
        </div> 
    </div>
</div>
</template>

<script>
import axios from "axios"

export default({
    props:{
        username:{
            type:String
        }
    },
    data(){
        return{
            user: {},
        }
    },
    method: {
        async fetchGitUsers(){
            try{
                const response = await axios.get(`https://api.github.com/users/${this.userame}`)
                this.user = response.data
            }
            catch(err){
                console.log('Error')
            }
        }
    },
    watch:{
        username:{
            immediate : true ,
            handler : function(){
                console.log(this.username)
                debugger
                this.fetchGitUsers()
            }
        }
    }
    
})
</script>