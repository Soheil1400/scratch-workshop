<script lang="ts">
	import { afterUpdate, onMount } from 'svelte';

	export let data;

	let pageContent: HTMLElement;

	afterUpdate(() => {
		import('scratchblocks').then(({ default: scratchblocks }) => {
			scratchblocks.renderMatching('pre.language-scratch', {
				style: 'scratch3',
				lang: 'en'
			});
		});
	});
</script>

<svelte:head>
	<title>{data.meta.title} — Scratch for Kids, Frontend Masters</title>
	<meta property="og:type" content="article" />
	<meta property="og:title" content={data.meta.title} />
</svelte:head>

<article>
	<hgroup>
		<h1>{data.meta.title}</h1>
	</hgroup>

	<div class="prose" bind:this={pageContent}>
		<svelte:component this={data.content} />
	</div>
	<footer class="flex justify-between mt-16 border-t-2 border-slate-200">
		<p>
			<a href="/" class="text-purple-800 underline decoration-black">&larr; برگشت</a>
		</p>
	</footer>
</article>
