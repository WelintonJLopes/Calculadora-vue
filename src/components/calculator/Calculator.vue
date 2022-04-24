<template>
	<v-container>
		Calculadora
		<Buttom />
		<Display />
	</v-container>
</template>

<script>
import Buttom from "./components/Buttom.vue";
import Display from "./components/Display.vue";

export default {
	name: "Calculator",
	components: { Buttom, Display },
};
</script>