<template>
	<div v-if="posts.length > 0">
		<post-item-vue 
		v-for='post of posts' 
		:key="post.id" 
		:post='post' 
		@remove="$emit('remove', post)"
		/>
</div>
<h1 v-else style='color : red'>Hет постов</h1>
</template>
<script>
import PostItemVue from './PostItem.vue';
export default {
	components: {
		PostItemVue
	},
	props: {
		posts: {
			type: Array,
			required: true
		}
	}
}
</script>
<style scoped>
h1 {
	margin-top: 20px;
	text-align: center;
	font-size: 32px;
}
</style>