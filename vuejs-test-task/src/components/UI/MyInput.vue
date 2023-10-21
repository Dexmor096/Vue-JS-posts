<template>
		<input   
			:value="modelValue"
			@input="updateInput"
      class='input' 
      type="text" 
      >
</template>
<script>
export default {
	name: 'my-input',
	props: {
		modelValue: {
			type: [String, Number]
		}
	},
	methods: {
		updateInput(event) {
			this.$emit('update:modelValue', event.target.value)
		}
	},
}
</script>
<style scoped>
	.input {
  padding: 10px;
  margin-bottom: 10px;
  color: teal;
  background-color: aliceblue;
}
</style>