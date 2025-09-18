<script lang="ts">
	import { Moi } from '$lib/components';
	import { Button } from '$lib/components/ui/button';
	import { SITE_LINKS } from '$lib/constants';
	import { Menu, X } from '@lucide/svelte';

	let open = $state(false);
</script>

<!-- Trigger Button -->
<Button
	variant="ghost"
	size="icon"
	onclick={() => {
		open = !open;
	}}
	>{#if open}
		<X class="size-7" />
	{:else}<Menu class="size-6" />{/if}</Button
>

{#if open}
	<div
		class="absolute top-16 left-0 flex h-[calc(100vh-64px)] w-full flex-col justify-between bg-background px-6 pb-12"
	>
		<div class="mt-[1em] flex flex-col gap-8">
			<span class="text-muted-foreground"
				>A software developer and film composer based in Toronto.</span
			>
			<!-- Main Links -->
			<div class="flex flex-col items-start gap-8">
				{#each SITE_LINKS as { href, label } (label)}
					<a {href} class="font-logo text-5xl font-medium tracking-wider"
						>{label}
						{#if label !== 'home'}<div>Soon</div>{/if}</a
					>
				{/each}
			</div>
		</div>

		<!-- Footer -->
		<Moi class="w-[30%]" />
	</div>
{/if}
