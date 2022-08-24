<template>
 
 <div>
  <b-navbar type="dark" variant="dark">
     <b-navbar-nav>
      
        <router-link to="/" class="nav-link">Home</router-link>
        <router-link to="/Historico" class="nav-link" >Historico</router-link>
        <b-form-input   @keyup="getUser" class="mr-sm-2" placeholder="Usuarios Github"></b-form-input>
     </b-navbar-nav>

  </b-navbar>
<p class="lead">Digite un nome para encontrar usuarios Github</p>

 <div class="row" v-if="user.length !==0 ">
<div class="col-md-4">
<Usuarios :user="user"/></div>


<div class="col-md-8">
  <Repositorio v-for="repo in repos" :key="repo" :repo="repo"   />
</div>
</div>
 </div>
</template>

<script>
// @ is an alias to /src
import Usuarios from '@/components/Usuarios.vue'
import Repositorio from '@/components/Repositorio.vue'
import axios from 'axios';


export default{
name: 'Home',
data(){
   return {
  github:{
  url:'https://api.github.com/users',
  client_id:'7eceaf34d17825837a31',
  client_secret:'fed6d3d1ba8d072ab67533ce06d0f3ec5566a399',
  count:7,
  sort:'created asc',
  },

   user:[],
   repos:[]
   };


},
components:   {
    Usuarios,
    Repositorio
    
},
     methods:{
     getUser(e)  {
       const user = e.target.value;
       const { url, client_id, client_secret, count, sort } = this.github;
       axios
       .get(
          `${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`
          )
          .then(({ data }) => (this.user= data));

         axios.get(`${url}/${user}/repos?per_page=${count}&sort=${sort}&client_id=${client_id}&client_secret=${client_secret}`
         )
         .then(({ data }) =>(this.repos = data));

     }
  }
};




</script>


<style scoped>
.col-md-4{

  background-color:#FDEBE7;
}

.btn{
margin-left: 5px;

}

.col-md-8{
background-color: black;

}
</style>
