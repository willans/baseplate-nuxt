<template>
	<div>
		<div
			v-for="(component, index) in $props.components"
			:key="index"
			:class="componentClass(index)"
		>
			<component
				:is="pascalCase(component.type)"
				v-if="$options.components[pascalCase(component.type)]"
				v-bind="lowerCaseProps(component.value)"
			/>

			<div
				v-else
				class="border border-blue p-5 overflow-scroll"
			>
				<span>component: {{ component.type }}</span>

				<div class="mt-4">
					<pre v-text="lowerCaseProps(component.value)" />
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import camelCase from 'lodash/camelCase';
	import upperFirst from 'lodash/upperFirst';

	// import Intro from '../builder/Intro';

	export default {
		components: {
			// Intro,
		},

		props: {
			components: {
				type: Array,
				default: null,
			},
		},

		methods: {
			pascalCase(name) {
				return upperFirst(camelCase(name));
			},

			lowerCaseProps(props) {
				const newObj = Object.fromEntries(
					Object.entries(props).map(([k, v]) => [k.toLowerCase(), v])
				);

				return newObj;
			},

			componentClass(index) {
				const spacing = index
					? 'mt-6 md:mt-8 xl:mt-10'
					: 'mt-10 md:mt-12 xl:mt-16';
				return spacing;
			},
		},
	};
</script>
