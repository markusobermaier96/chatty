<script lang="ts">
	import MarkdownIt from 'markdown-it'
	import type { ChatCompletionRequestMessageRoleEnum } from 'openai'
	const md = new MarkdownIt()

	export let role: ChatCompletionRequestMessageRoleEnum
	export let content: string
</script>

<div class={role === 'user' ? 'flex flex-col p-3 bg-blue-200' : 'flex flex-col p-3 bg-gray-100'}>
	{#if role === 'user'}
		<svg
			xmlns="http://www.w3.org/2000/svg"
			fill="currentColor"
			viewBox="0 0 24 24"
			stroke-width="1.5"
			stroke="currentColor"
			class="w-8 h-8 mr-4"
		>
			<path
				stroke-linecap="round"
				stroke-linejoin="round"
				d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z"
			/>
		</svg>
	{:else}
		<img class="w-8 h-8 mr-4" src="bot-image.png" alt="bot-icon" />
	{/if}
	{@html md.render(content)}
</div>
