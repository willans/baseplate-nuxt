<template>
	<div class="x-container text-center max-w-2xl">
		<h1
			class="x-h3"
			v-text="$props.title"
		/>

		<p
			class="mt-4"
			v-text="$props.content"
		/>
	</div>
</template>

<script>
	export default {
		props: {
			title: {
				type: String,
				default: null,
			},

			content: {
				type: String,
				default: null,
			},
		},
	};
</script>
