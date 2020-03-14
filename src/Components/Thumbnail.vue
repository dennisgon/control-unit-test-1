<template>
	<div class="card">
		<img class="card-img-top" v-bind:src="image" alt="Card image cap">
		<div class="card-body">
			<h5 class="card-title">{{ title }}</h5>
			<p class="card-text">{{ description }}</p>
		</div>
	</div>	
</template>

<script>
	export default {
	  	name: 'thumbnail',
	 	props:['title', 'image', 'description']
	}
</script>

<style scoped>
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
  height: 200px;
  width: 200px;
}
.card-title{
	text-align: center;
}
.card-text{
	text-align: center;
}

</style>