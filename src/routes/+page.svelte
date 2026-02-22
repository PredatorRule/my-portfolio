<script lang="ts">
	import { fly, fade } from 'svelte/transition';
	import { onMount } from 'svelte';

	let mounted = $state(false);
	
	// Typewriter Logic
	let dynamicWord = $state("");
	let fullSentence = $state("");
	let isFinalState = $state(false);
	
	const words = ["zero-downtime platforms", "self-healing systems", "frictionless CI/CD"];
	const finalPart = "resilient, automated cloud infrastructure powering global automotive innovation.";

	// Phantom Node System
	let particles = $state<{x: number, y: number, size: number, bg: string, shadow: string, duration: number, delay: number}[]>([]);
	
	const particleTypes = [
		{ bg: 'bg-[#00f2fe]', shadow: 'rgba(0, 242, 254, 0.8)' },
		{ bg: 'bg-blue-500', shadow: 'rgba(59, 130, 246, 0.8)' },
		{ bg: 'bg-indigo-400', shadow: 'rgba(129, 140, 248, 0.8)' }
	];

	onMount(() => {
		mounted = true;
		runTypewriter();

		// Generate 70 stealthy phantom nodes
		particles = Array.from({ length: 70 }).map(() => {
			const type = particleTypes[Math.floor(Math.random() * particleTypes.length)];
			return {
				x: Math.random() * 100,
				y: Math.random() * 100,
				size: Math.random() * 2 + 1.5,
				bg: type.bg,
				shadow: type.shadow,
				duration: Math.random() * 15 + 10, // 10s to 25s
				delay: Math.random() * -30 // Staggered start times
			};
		});
	});

	async function runTypewriter() {
		for (const word of words) {
			for (let i = 0; i <= word.length; i++) {
				dynamicWord = word.slice(0, i);
				await new Promise(r => setTimeout(r, 80));
			}
			await new Promise(r => setTimeout(r, 1200));
			for (let i = word.length; i >= 0; i--) {
				dynamicWord = word.slice(0, i);
				await new Promise(r => setTimeout(r, 40));
			}
		}

		isFinalState = true;
		for (let i = 0; i <= finalPart.length; i++) {
			fullSentence = finalPart.slice(0, i);
			await new Promise(r => setTimeout(r, 50));
		}
	}

	// Scroll Reveal Action
	function reveal(node: HTMLElement) {
		node.style.opacity = '0';
		node.style.transform = 'translateY(40px)';
		node.style.transition = 'all 0.8s cubic-bezier(0.16, 1, 0.3, 1)';
		
		const observer = new IntersectionObserver((entries) => {
			if (entries[0].isIntersecting) {
				node.style.opacity = '1';
				node.style.transform = 'translateY(0)';
				observer.unobserve(node);
			}
		}, { threshold: 0.15 });
		
		observer.observe(node);
		return { destroy() { observer.disconnect(); } };
	}

	// Data
	const techIcons = [
		{ name: "AWS", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" },
		{ name: "Google Cloud", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/googlecloud/googlecloud-original.svg" },
		{ name: "Terraform", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/terraform/terraform-original.svg" },
		{ name: "Ansible", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/ansible/ansible-original.svg" },
		{ name: "Jenkins", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/jenkins/jenkins-original.svg" },
		{ name: "Prometheus", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/prometheus/prometheus-original.svg" },
		{ name: "Grafana", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/grafana/grafana-original.svg" },
		{ name: "Elasticsearch", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/elasticsearch/elasticsearch-original.svg" }
	];

	const programmingLangs = [
		{ name: "Python", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" },
		{ name: "Java", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg" },
		{ name: "Bash", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bash/bash-original.svg" },
		{ name: "Spring Boot", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/spring/spring-original.svg" },
		{ name: "Svelte", url: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/svelte/svelte-original.svg" }
	];

	const softSkills = ["Team player", "Problem-solving", "Critical thinking", "Strong work ethic", "Detail oriented", "Adaptability", "Emotional intelligence", "Time management"];
	const spokenLanguages = [{ name: "Portuguese", level: "Native" }, { name: "English", level: "Advanced" }];
</script>

<div class="fixed inset-0 z-0 pointer-events-none bg-[#030712] overflow-hidden">
	<div class="absolute inset-0 bg-[linear-gradient(to_right,#4f4f4f20_1px,transparent_1px),linear-gradient(to_bottom,#4f4f4f20_1px,transparent_1px)] bg-[size:40px_40px] [mask-image:radial-gradient(ellipse_80%_80%_at_50%_0%,#000_40%,transparent_100%)]"></div>
	
	<div class="absolute inset-0">
		{#each particles as p}
			<div 
				class="absolute rounded-full {p.bg} mix-blend-screen phantom-dot"
				style="
					left: {p.x}%; 
					top: {p.y}%; 
					width: {p.size}px; 
					height: {p.size}px; 
					box-shadow: 0 0 {p.size * 3}px {p.shadow}; 
					--dur: {p.duration}s;
					--del: {p.delay}s;
				"
			></div>
		{/each}
	</div>
</div>

{#if mounted}
<div class="relative z-10 space-y-40 pb-40 px-6">
	
	<section class="min-h-screen flex flex-col justify-center items-center text-center">
		<h1 in:fly={{ y: 50, duration: 1000 }} class="text-7xl md:text-9xl font-black tracking-tighter mb-4 text-white uppercase drop-shadow-2xl">
			JOÃO <span class="text-transparent bg-clip-text bg-gradient-to-r from-[#00f2fe] to-blue-500">FERREIRA</span>
		</h1>
		
		<div in:fly={{ y: 20, delay: 400 }} class="flex flex-col items-center gap-6">
			<h2 class="text-2xl md:text-4xl font-bold text-[#00f2fe] tracking-tight">
				Cloud Platform & DevOps Engineer
			</h2>
			
			<div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-gray-950/50 border border-[#00f2fe]/30 text-[#00f2fe] font-bold text-xs tracking-widest uppercase shadow-[0_0_15px_rgba(0,242,254,0.1)] backdrop-blur-md">
				<span class="relative flex h-2 w-2">
					<span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-[#00f2fe] opacity-75"></span>
					<span class="relative inline-flex rounded-full h-2 w-2 bg-[#00f2fe]"></span>
				</span>
				Status: Evolving @ VWDS
			</div>

			<p class="text-gray-300 max-w-2xl text-lg md:text-xl font-medium min-h-[1.5em] font-mono">
				Architecting <span class="text-white">{isFinalState ? fullSentence : dynamicWord}</span><span class="animate-blink text-[#00f2fe] font-bold">|</span>
			</p>
		</div>

		<div in:fade={{ delay: 1200 }} class="mt-12 flex flex-wrap justify-center gap-4">
			<a href="mailto:joaopsferreira92@gmail.com" class="px-8 py-4 rounded-xl bg-[#00f2fe] text-black font-black hover:scale-105 transition-transform shadow-[0_0_20px_rgba(0,242,254,0.4)]">
				Hire Me
			</a>
			<a href="#tech" class="px-8 py-4 rounded-xl border border-[#00f2fe]/40 text-[#00f2fe] hover:bg-[#00f2fe]/10 transition-colors font-bold backdrop-blur-sm bg-gray-900/40">
				My Tech Stack
			</a>
			<a href="#journey" class="px-8 py-4 rounded-xl border border-gray-600 hover:border-gray-400 transition-colors font-bold text-gray-300 backdrop-blur-sm bg-gray-900/40">
				My Career
			</a>
		</div>
	</section>

	<section id="tech" class="max-w-6xl mx-auto">
		<div use:reveal class="text-center mb-16">
			<h2 class="text-5xl font-bold text-white mb-4">Skills & Tech Stack</h2>
			<div class="w-16 h-1 bg-[#00f2fe] mx-auto"></div>
		</div>

		<div use:reveal class="flex flex-wrap justify-center items-center gap-12 md:gap-20 mb-20">
			{#each techIcons as icon}
				<div class="group flex flex-col items-center gap-4 cursor-default w-24">
					<img src={icon.url} alt="{icon.name} logo" class="w-16 h-16 transition-all duration-500 transform group-hover:scale-110 filter grayscale opacity-50 group-hover:grayscale-0 group-hover:opacity-100 drop-shadow-none group-hover:drop-shadow-[0_0_25px_rgba(0,242,254,0.4)]" />
					<span class="text-gray-400 font-mono text-sm font-bold opacity-0 group-hover:opacity-100 group-hover:text-[#00f2fe] transition-all duration-300 translate-y-2 group-hover:translate-y-0 text-center">{icon.name}</span>
				</div>
			{/each}
		</div>

		<div class="w-full max-w-4xl mx-auto border-t border-gray-800/80 mb-12"></div>

		<div use:reveal class="flex flex-col items-center text-center mb-24">
			<h3 class="text-gray-400 font-mono text-lg mb-8">Programming Languages <span class="text-[#00f2fe] font-bold">& Frameworks</span></h3>
			
			<div class="flex flex-wrap justify-center gap-4 max-w-3xl">
				{#each programmingLangs as lang}
					<div class="flex items-center gap-3 px-5 py-2.5 bg-gray-900/60 border border-gray-700/50 rounded-xl hover:border-[#00f2fe]/60 transition-all group cursor-default shadow-xl shadow-black/50 backdrop-blur-md">
						<img src={lang.url} alt={lang.name} class="w-5 h-5 filter grayscale group-hover:grayscale-0 transition-all duration-300" />
						<span class="text-gray-300 group-hover:text-white font-medium text-sm transition-colors">{lang.name}</span>
					</div>
				{/each}
			</div>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-16 border-t border-gray-800/80 pt-16">
			<div use:reveal class="flex flex-col items-center text-center">
				<h3 class="text-gray-400 font-mono uppercase tracking-[0.2em] mb-8 text-sm">Soft Skills</h3>
				<div class="flex flex-wrap justify-center gap-3">
					{#each softSkills as skill}
						<span class="px-5 py-2 bg-gray-900/50 border border-gray-700/50 rounded-lg text-gray-300 font-medium hover:border-[#00f2fe]/60 hover:text-[#00f2fe] transition-all shadow-md backdrop-blur-sm">
							{skill}
						</span>
					{/each}
				</div>
			</div>

			<div use:reveal class="flex flex-col items-center text-center">
				<h3 class="text-gray-400 font-mono uppercase tracking-[0.2em] mb-8 text-sm">Languages</h3>
				<div class="flex flex-wrap justify-center gap-4">
					{#each spokenLanguages as lang}
						<div class="px-8 py-3 bg-gray-900/50 border border-gray-700/50 rounded-lg flex flex-col hover:border-[#00f2fe]/60 transition-all group backdrop-blur-sm shadow-md">
							<span class="text-gray-200 group-hover:text-white font-bold">{lang.name}</span>
							<span class="text-[#00f2fe] text-xs font-mono uppercase mt-1">{lang.level}</span>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</section>

	<section id="journey" class="max-w-4xl mx-auto">
		<div use:reveal class="text-center mb-20">
			<h2 class="text-5xl font-bold text-white mb-4">Career Timeline</h2>
			<div class="w-16 h-1 bg-[#00f2fe] mx-auto"></div>
		</div>
		
		<div class="relative border-l-2 border-[#00f2fe]/30 ml-4 space-y-24">
			<div use:reveal class="relative pl-12 group">
				<div class="absolute w-5 h-5 bg-[#00f2fe] rounded-full -left-[11px] top-1 shadow-[0_0_15px_rgba(0,242,254,0.8)]"></div>
				<div class="p-8 bg-gray-900/50 border border-gray-700/50 rounded-2xl hover:border-[#00f2fe]/60 transition-all hover:-translate-y-1 backdrop-blur-xl shadow-2xl">
					<div class="flex flex-col md:flex-row justify-between md:items-center gap-2 mb-4">
						<h3 class="text-2xl font-bold text-white">Platform/Support Engineer</h3>
						<span class="text-[#00f2fe] font-mono text-sm">Sept 2025 — Present</span>
					</div>
					<p class="text-gray-200 font-bold mb-4">Volkswagen Digital Solutions</p>
					<p class="text-gray-400 text-sm leading-relaxed">Engineering resilient platform solutions and cloud automation for global automotive scale.</p>
				</div>
			</div>

			<div use:reveal class="relative pl-12">
				<div class="absolute w-4 h-4 bg-gray-800 rounded-full -left-[9px] top-1 border-2 border-gray-500"></div>
				<div class="p-8 bg-gray-900/40 border border-gray-700/50 rounded-2xl hover:border-gray-400 transition-all hover:-translate-y-1 backdrop-blur-md shadow-lg">
					<div class="flex flex-col md:flex-row justify-between md:items-center gap-2 mb-4">
						<h3 class="text-2xl font-bold text-white">DevOps Engineer</h3>
						<span class="text-gray-400 font-mono text-sm">Dec 2022 — Aug 2025</span>
					</div>
					<p class="text-gray-200 font-bold mb-4">Broadvoice</p>
					<ul class="text-gray-400 text-sm space-y-2">
						<li>• Automated CI/CD pipelines utilizing Jenkins and GitHub Actions.</li>
						<li>• Deployed and managed AWS EKS clusters with Terraform and Ansible.</li>
						<li>• Implemented monitoring via Prometheus, Thanos, and Grafana.</li>
					</ul>
				</div>
			</div>

			<div use:reveal class="relative pl-12">
				<div class="absolute w-4 h-4 bg-gray-800 rounded-full -left-[9px] top-1 border-2 border-gray-500"></div>
				<div class="p-8 bg-gray-900/30 border border-gray-700/50 rounded-2xl hover:border-gray-400 transition-all hover:-translate-y-1 backdrop-blur-sm shadow-lg">
					<div class="flex flex-col md:flex-row justify-between md:items-center gap-2 mb-4">
						<h3 class="text-xl font-bold text-white">IT Platform Support / DevOps</h3>
						<span class="text-gray-400 font-mono text-sm">Oct 2021 — Jun 2023</span>
					</div>
					<p class="text-gray-400 text-sm">Leonteq • Lisboa, Portugal</p>
				</div>
			</div>
		</div>
	</section>
</div>
{/if}

<style>
	:global(html) {
		background-color: #030712;
		scroll-behavior: smooth;
	}

	/* Terminal Cursor */
	@keyframes blink {
		0%, 100% { opacity: 1; }
		50% { opacity: 0; }
	}
	.animate-blink {
		animation: blink 1s step-end infinite;
	}

	/* Bulletproof Phantom Node Animation mapped to CSS variables */
	.phantom-dot {
		opacity: 0; /* Fallback base state */
		animation-name: phantomNode;
		animation-duration: var(--dur);
		animation-timing-function: ease-in-out;
		animation-iteration-count: infinite;
		animation-delay: var(--del);
	}

	@keyframes phantomNode {
		0% { 
			opacity: 0; 
			transform: scale(0.5);
		}
		50% { 
			opacity: 0.5; /* Bright enough to see, faint enough to blend */
			transform: scale(1);
		}
		100% { 
			opacity: 0; 
			transform: scale(0.5);
		}
	}
</style>