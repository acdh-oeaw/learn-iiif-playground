<script lang="ts" setup>
const props = defineProps<{
	targetId: string;
}>();

const route = useRoute();

/**
 * @see https://bugzilla.mozilla.org/show_bug.cgi?id=308064
 */
function onClick() {
	const element = document.getElementById(props.targetId);
	element?.focus();
}
</script>

<template>
	<NuxtLink
		class="text-on-background fixed -translate-y-full rounded bg-background px-4 py-3 transition focus:translate-y-0"
		:href="{ hash: `#${props.targetId}`, query: route.query }"
		@click="onClick"
	>
		<slot />
	</NuxtLink>
</template>
