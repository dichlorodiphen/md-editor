<script lang="ts">
	import './styles.css';

	import DOMPurify from 'isomorphic-dompurify';
	import { marked } from 'marked';
	import { onMount } from 'svelte';

	let textarea: HTMLTextAreaElement;

	let markdown: string = `# Markdown!\n\nTry replacing this text with something else!\n\n* This\n* is\n* nice.`;

	onMount(() => {
		textarea.focus();
	});

	function render(markdown: string): string {
		return marked(DOMPurify.sanitize(markdown), { async: false }) as string;
	}
</script>

<div class="all-content">
	<div class="editor">
		<textarea class="editor__textarea" bind:this={textarea} bind:value={markdown}></textarea>
	</div>
	<div class="render">{@html render(markdown)}</div>
</div>

<style>
	.all-content {
		display: grid;
		grid-template-columns: 1fr 1fr;
		width: 100%;
		height: 100%;

		/* Typography */
		font-size: 2rem;
		font-family: 'IBM Plex Mono', monospace;
		line-height: 1.3;
	}

	.editor__textarea {
		width: 100%;
		height: 100%;
		padding: 2rem;

		/* Typography */
		font-size: inherit;
		font-family: inherit;
		line-height: inherit;

		/* Border */
		border: none;
		border-right: 2px solid #909090;

		&:focus {
			outline: none;
		}
	}

	.render {
		padding: 2rem;

		/* Typography */
		line-height: 1.6;

		& input {
			vertical-align: middle;
		}
	}
</style>
