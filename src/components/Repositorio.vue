<template>
<div class="card card-body mb-2">
<div class="row"> 
<div class="col-md-6">
<a :href="repo.html_url" target="_blank">{{repo.name}}</a>
</div>	
<div id="repo">
  <span class="w3-badge w3-blue">Stars: {{ repo.stargazers_count }}</span>
  <span class="w3-badge w3-yellow">Watch: {{ repo.watchers_count }}</span>
  <span class="w3-badge w3-red">Forks: {{repo.forks_count}}</span>
</div>
</div>
</div>
</template>
<script>
export default {
  props:['repo']
};
</script>


<style scoped>

.a{


  color: #010101;
    text-decoration: underline;
    font-family: cursive;
}

</style>