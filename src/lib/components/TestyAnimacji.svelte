<script>
	import BlurFade from '$lib/components/BlurFade.svelte';
	import FlipText from '$lib/components/FlipText.svelte';
	import WordRotate from '$lib/components/WordRotate.svelte';
</script>

<section id="header">
	<BlurFade delay={0.25}>
		<h2 class="text-3xl font-bold tracking-tighter sm:text-5xl xl:text-6xl/none">Hello World 👋</h2>
	</BlurFade>
	<BlurFade delay={0.25 * 2}>
		<span class="text-xl text-pretty tracking-tighter sm:text-3xl xl:text-4xl/none">
			Nice to meet you
		</span>
	</BlurFade>
</section>

<br />

<FlipText
	class="text-4xl font-bold tracking-[-0.1em] text-black dark:text-white md:text-7xl md:leading-[5rem]"
	word="Flip Text"
/>

<div class="flex justify-center items-center min-h-40">
	<WordRotate
		class="text-4xl font-bold text-black dark:text-white"
		words={['Svelte', 'Is', '🪄Vibe']}
	/>
</div>

<div class="flex justify-center items-center h-[80vh] w-full">
	<div
		class="relative flex h-fit w-full max-w-[32rem] items-center justify-center overflow-hidden rounded-lg border bg-background px-40 pb-40 pt-8 md:pb-60 md:shadow-xl"
	>
		<span
			class="pointer-events-none select-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-8xl font-semibold leading-none text-transparent dark:from-white dark:to-slate-900/10"
		>
			Globe
		</span>
	</div>
</div>
