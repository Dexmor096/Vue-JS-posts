<template lang="">
	<div class='post' >
		<div>
			<h1>Новый пост</h1>
			<div	class='post_line'><strong>Post: </strong>{{ post.title }}</div>
			<div	class='post_line'><strong>Post: </strong>{{ post.body }}</div>
		</div>
		<my-button
			@click="$emit('remove', post)"
		>Удалить</my-button>
	</div>
</template>
<script>
export default {

	props: {
		post: {
			type: Object,
			required: true
		}
	}
}
</script>
<style scoped>
	.post {
		display: flex;
		justify-content: space-between;
		align-items: center;
		flex-direction: row;
		margin-top: 15px;
		padding: 15px;
		border: 2px solid teal;
}
.post_line {
	padding-top: 5px;
}
</style>