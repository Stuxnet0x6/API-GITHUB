<template>
	<div>
	  <div class="row">
		<div id="col-md-4">
		   <div id="card" style="width: 18rem;">
		 	<img class="card-img-top" :src="user.avatar_url"/>
	<ul class="lis-group list-group-flush">

        <li class="list-group-item">Repos: <span class="w3-badge w3-yellow">{{ user.public_repos }}</span></li>
        <li class="list-group-item">seguidores:<span class="w3-badge w3-red">{{ user.followers }}</span></li>
        <li class="list-group-item">seguindo:<span class="w3-badge w3-green">{{ user.following }}</span></li>
         </ul>
         <div class="card-body">
         	<a :href="user.html_url" class="btn btn-success btn-block">ver perfil</a>
         </div>
       </div>	
    </div>
    
    </div>
	</div>
</template>

<script>
	export default{
    
       props: ["user"]

	};
</script>

<style scoped>
.babge .bange-succes{
color:red;


}
</style>