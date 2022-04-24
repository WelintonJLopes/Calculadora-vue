<template>
	<v-col :cols="cols * 3" style="border: 1px solid black">
		<v-btn
			@click="$emit('onClick', label)"
			elevation="0"
			tile
			class="rounded-0"
			:class="operation ? 'orange white--text' : 'white'"
			block
			x-large
		>{{label}}</v-btn>
	</v-col>
</template>

<script>
export default {
	name: "Button",
	props: ["label", "cols", "operation"],
};
</script>

<style>
</style>