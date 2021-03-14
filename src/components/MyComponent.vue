<template>
<div>
	<h1> Some shit from my Component</h1>
	<h2>{{data}}</h2>
</div>
</template>

<script>
// import { defineComponent } from '@vue/composition-api'

export default {
	props:{
		data: [Object]
	}
};
</script>
