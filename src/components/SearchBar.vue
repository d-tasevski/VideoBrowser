<template>
	<div class="search-bar">
		<input @input="onInput" type="text" placeholder="Search">
	</div>
</template>

<script>
export default {
	name: 'SearchBar',
	methods: {
		onInput(e) {
			this.$emit('termChange', e.target.value);
		},
	},
};
</script>

<style scoped>
input {
	width: 75%;
	padding: 0 1rem;
}
.search-bar {
	text-align: center;
	margin: 1rem;
}
</style>
