<script lang="ts">
	import { cn } from '$lib/utils';

	type Props = {
		class?: string;
	};

	let { class: className }: Props = $props();
</script>

<div class={cn('shape flex aspect-square items-center justify-center', className)}>
	<img src="./me.JPG" alt="Geoffrey Belcher" class="aspect-square w-[90%] rounded-full border-8" />
</div>

<style>
	.shape {
		background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
		background-size: 400% 400%;
		animation: morph 5s ease-in-out infinite;
		border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
		transition: morph 1s ease-in-out;
	}

	@keyframes morph {
		0% {
			border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
			background-position: 0% 50%;
		}

		50% {
			border-radius: 30% 60% 70% 40% / 50% 60% 30% 60%;
			background-position: 100% 50%;
		}

		100% {
			border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
			background-position: 0% 50%;
		}
	}
</style>
