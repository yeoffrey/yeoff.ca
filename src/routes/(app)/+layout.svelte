<script lang="ts">
	import type { LayoutProps } from './$types';
	import { MobileNav, Moi, ThemeToggle } from '$lib/components';
	import { SITE_LINKS } from '$lib/constants';
	import { Badge } from '$lib/components/ui/badge';

	let { children }: LayoutProps = $props();
</script>

<!-- Navigation bar for small screens -->
<div class="lg:hidden">
	<div class="flex h-16 flex-row items-center justify-between bg-background px-6">
		<span class="font-logo text-4xl">yeoff.ca</span>
		<div class="flex flex-row items-center gap-4">
			<ThemeToggle />
			<MobileNav />
		</div>
	</div>
	<main class="px-6">
		{@render children?.()}
	</main>
</div>

<!-- Sidebar layout for large screens -->
<div class="hidden items-center justify-center p-16 lg:flex">
	<div
		class="flex h-[80vh] max-w-[85%] gap-4 rounded-xl border-7 border-double p-16 shadow-2xl shadow-accent"
	>
		<aside class="flex w-1/5 flex-col justify-between">
			<div class="flex flex-col gap-8">
				<span class="font-logo text-6xl">yeoff.ca</span>
				<span class="text-muted-foreground"
					>A software developer and film composer based in Toronto.</span
				>
			</div>

			<!-- Main Links -->
			<div class="flex flex-col items-start gap-2">
				{#each SITE_LINKS as { href, label } (label)}
					{@const disabled = label !== 'home'}
					<div class="flex items-center gap-2">
						<a
							{href}
							class={`font-logo text-4xl font-medium tracking-wider hover:underline ${disabled ? 'pointer-events-none cursor-not-allowed opacity-50' : ''}`}
							>{label}
						</a>
						{#if label !== 'home'}<Badge
								variant="secondary"
								class="bg-blue-500 text-white opacity-50 dark:bg-blue-600">Soon</Badge
							>{/if}
					</div>
				{/each}
			</div>

			<!-- Footer -->
			<Moi class="w-[60%]" />
		</aside>
		<main class="relative w-4/5">
			<ThemeToggle class="absolute top-0 right-0 z-5" />
			<div class="mx-auto max-w-[80%]">
				{@render children?.()}
			</div>
		</main>
	</div>
</div>
