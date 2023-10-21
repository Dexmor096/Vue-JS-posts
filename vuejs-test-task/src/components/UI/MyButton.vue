<template lang="">
	<button class='btn__main'>
		<slot></slot>
	</button>
</template>
<script>
export default {
	name: 'my-button'
}
</script>
<style scoped>
	.btn__main {
		width: 100px;
		height: 50px;
		padding: 5px 10px;
		background: none;
		border: 1px solid teal;
		cursor: pointer;
}
</style>