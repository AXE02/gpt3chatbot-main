<script lang="ts">
	import ChatMessage from '$lib/components/ChatMessage.svelte'
	import type { ChatCompletionRequestMessage } from 'openai'
	import { SSE } from 'sse.js'

	let query: string = ''
	let answer: string = ''
	let loading: boolean = false
	let chatMessages: ChatCompletionRequestMessage[] = []
	let scrollToDiv: HTMLDivElement

	function scrollToBottom() {
		setTimeout(function () {
			scrollToDiv.scrollIntoView({ behavior: 'smooth', block: 'end', inline: 'nearest' })
		}, 100)
	}

	const handleSubmit = async () => {
		loading = true
		chatMessages = [...chatMessages, { role: 'user', content: query }]

		const eventSource = new SSE('/api/chat', {
			headers: {
				'Content-Type': 'application/json'
			},
			payload: JSON.stringify({ messages: chatMessages })
		})

		query = ''

		eventSource.addEventListener('error', handleError)

		eventSource.addEventListener('message', (e) => {
			scrollToBottom()
			try {
				loading = false
				if (e.data === '[DONE]') {
					chatMessages = [...chatMessages, { role: 'assistant', content: answer }]
					answer = ''
					return
				}

				const completionResponse = JSON.parse(e.data)
				const [{ delta }] = completionResponse.choices

				if (delta.content) {
					answer = (answer ?? '') + delta.content
				}
			} catch (err) {
				handleError(err)
			}
		})
		eventSource.stream()
		scrollToBottom()
	}

	function handleError<T>(err: T) {
		loading = false
		query = ''
		answer = ''
		console.error(err)
	}
</script>
<style>

@import url('https://fonts.googleapis.com/css2?family=Golos+Text&family=Syne:wght@800&display=swap');
.sendbtn{
	background: #011AFC;
}
.inptbx{
	background: #FFFFFF;
    box-shadow: 0px -4px 12px rgba(0, 0, 0, 0.07);
	position:sticky;
	bottom:0;
}
.inpt{
	background: #F2F2F2;
}
.bdy{
	width:100%;
height:100pc;
}
.mascot{
	width:304px;
	margin-top:0;
}
.prjct{
font-family: 'Syne', sans-serif;
margin-top:-23px;
font-style: bold;
font-weight: 800;
font-size: 50px;
line-height: 120%;
}
.prjct2{
font-family: 'Golos Text', sans-serif;
font-style: normal;
font-weight: 500;
font-size: 18px;
line-height: 26px;
width:343px;
text-align: center;

color: #FFFFFF;

opacity: 0.6;
}
.msdiv{
	width:430px;
	padding:20px;
}
.bdy1{
	display:flex;
	width:100%;
height:100pc;
}


</style>
<div class="bdy1">
<div class="msdiv">
<center>
<img class="mascot" src="/mascot.png">
<p class="prjct">KABIR</p>
<p class="prjct2">Knowledgeable AI Bot for Investigating and Resolving cybercrimes</p>
</center>
</div>

<div class="bdy">
	<div class="h-[520px] bdy bg-white rounded-md p-4 overflow-y-auto  ">
		<div class="flex flex-col gap-2">
			<ChatMessage type="assistant" message="Hello, ask me anything you want!" />
			{#each chatMessages as message}
				<ChatMessage type={message.role} message={message.content} />
			{/each}
			{#if answer}
				<ChatMessage type="assistant" message={answer} />
			{/if}
			{#if loading}
				<ChatMessage type="assistant" message="Loading.." />
			{/if}
		</div>
		<div class="" bind:this={scrollToDiv} />
	</div> 
	<form
		class="flex inptbx w-full rounded-md gap-4 bg-gray-900 p-4"
		on:submit|preventDefault={() => handleSubmit()}
	>
	<input type="text" class="input inpt input-bordered w-full" bind:value={query} placeholder="Type your message here" style="color: black;"/>
		<button type="submit" class="btn sendbtn btn-accent"> Send </button>
	</form>

</div>
</div>
