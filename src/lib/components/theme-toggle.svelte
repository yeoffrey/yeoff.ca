<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { cn } from '$lib/utils';
	import { Moon, Sun } from '@lucide/svelte';
	import { toggleMode } from 'mode-watcher';

	type Props = {
		class?: string;
	};

	let { class: className }: Props = $props();
</script>

<Button onclick={toggleMode} variant="ghost" size="icon" class={cn('', className)}>
	<Sun class="size-5 scale-100 rotate-0 !transition-all dark:scale-0 dark:-rotate-90" />
	<Moon class="absolute size-5 scale-0 rotate-90 !transition-all dark:scale-100 dark:rotate-0" />
	<span class="sr-only">Toggle theme</span>
</Button>
