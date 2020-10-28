<template>
	<div>
		<page-builder :components="$data.model.pageBuilder" />
	</div>
</template>

<script>
	import head from '../../assets/js/mixins/head';

	export default {
		mixins: [head],

		async asyncData ({ $content }) {
			return await $content('about').fetch();
		},

	};
</script>
