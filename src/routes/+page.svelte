<script lang="ts">
	import './styles.css';

	import DOMPurify from 'isomorphic-dompurify';
	import { marked } from 'marked';
	import { onMount } from 'svelte';

	let textarea: HTMLTextAreaElement;

	onMount(() => {
		textarea.focus();
	});
</script>

<div class="all-content">
	<div class="editor">
		<textarea class="editor__textarea" bind:this={textarea}></textarea>
	</div>
	<div class="render">rendered text goes here</div>
</div>

<style>
	.all-content {
		display: grid;
		grid-template-columns: 1fr 1fr;
		width: 100%;
		height: 100%;
		background-color: orangered;
	}

	.editor {
		/* TODO */
	}

	.editor__textarea {
		width: 100%;
		height: 100%;
		padding: 2rem;
	}

	.render {
		font-size: 2rem;
		padding: 2rem;
	}
</style>
