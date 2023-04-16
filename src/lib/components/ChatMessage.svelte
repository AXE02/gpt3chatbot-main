<script lang="ts">
	import type { ChatCompletionRequestMessageRoleEnum } from 'openai'
	export let type: ChatCompletionRequestMessageRoleEnum
	export let message: string
</script>
<style>
body{
	
}
.chat{
	width:80%;
	background-color:white;

}
.mrgn{
		margin-left:100px;
}	
.chat-bubbl{
	padding: 12px 16px;
	background: #EBF1FC;
    border-radius: 10px;
	color: #070A25;

}
.chat-bubbl-primary{
	color: #FFFFFF;
	background: #011AFC;
	right:0px;
}
</style>

<div class="chat {type === 'user' ? 'chat-end mrgn' : 'chat-start'} justify-end">
	
	<div class="chat-header">
		{type === 'user' ? 'Me' : 'Bot'}
	</div>
	<div class="chat-bubbl {type === 'user' ? 'chat-bubbl-primary' : 'chat-bubbl-secondary'}">
		{message}
	</div>
</div>
