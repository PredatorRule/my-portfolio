<script lang="ts">
	import './layout.css';
	import '../app.css';

	let { children } = $props();
</script>

<div
	class="min-h-screen bg-gray-950 font-sans text-gray-100 selection:bg-cyan-500 selection:text-white"
>
	<nav class="sticky top-0 z-50 border-b border-gray-800 bg-gray-950/80 backdrop-blur-md">
		<div class="mx-auto flex max-w-5xl items-center justify-between px-6 py-4">
			<a href="/" class="text-xl font-bold tracking-tighter transition-colors hover:text-cyan-400"
				>Joao<span class="text-cyan-500">.devops</span></a
			>

			<div class="flex gap-6 text-sm font-medium text-gray-400">
				<a href="#journey" class="transition-colors hover:text-white">Journey</a>

				<a href="#projects" class="transition-colors hover:text-white">Projects</a>
			</div>
		</div>
	</nav>

	<main class="mx-auto max-w-5xl px-6 py-12">{@render children()}</main>

	<footer class="mt-20 border-t border-gray-800 py-8 text-center text-sm text-gray-500">
		<p>Built with SvelteKit & OpenTofu. Deployed on Cloudflare.</p>
	</footer>
</div>
