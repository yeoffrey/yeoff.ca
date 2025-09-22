<script lang="ts">
	import { cn } from '$lib/utils';
	import type { Snippet } from 'svelte';

	type Props = {
		label?: string;
		class?: string;
		children?: Snippet;
	};

	let { class: className, label, children }: Props = $props();
</script>

<div class={cn('relative m-1 border-2 p-2', className)}>
	{#if label}
		<span class="absolute -top-3 left-2 bg-background px-1 text-sm text-muted-foreground"
			>{label}</span
		>
	{/if}
	{@render children?.()}
</div>
