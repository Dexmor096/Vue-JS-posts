<template>
	<div 
	class="popup__wrapper"
	v-if="showPopup"
	v-on:click='hidePopup'
	>
		<div class='popup__inner' @:click.stop>
			<slot></slot>
		</div>
	</div>
</template>
<script>
export default {
	name: 'my-popup',
	props: {
		showPopup: {
			type: Boolean,
			default: false
		}
	},
	methods: {
		hidePopup() {
      this.$emit('update:showPopup', false)
    }
	},
}
</script>
<style scoped>
	.popup__wrapper{
		display: flex;
		justify-content: center;
		align-items: center;
		position: fixed;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		z-index: 10;
		background: rgba(0,0,0,0.5);
		margin: auto;
	}
	.popup__inner {
		background-color: #fbf8f8;
		min-height: 230px;
		min-width: 350px;
		border-radius: 5px;
		padding: 15px 30px;
		box-shadow: 0 0 10px #777;
	}
</style>