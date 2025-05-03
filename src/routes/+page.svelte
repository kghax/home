<script lang="ts">
	const linkGroups = [
		{
			name: 'LLM',
			links: [
				{
					name: 'Gemini',
					description: 'Geminiのチャット画面',
					url: 'https://gemini.google.com/app?hl=ja',
					network: 'public'
				},
				{
					name: 'Google AI Studio',
					description: 'GeminiのAPIキー管理',
					url: 'https://aistudio.google.com/u/0/apikey?pli=1',
					network: 'public'
				}
			]
		}
	];
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div id="hero" style="background-image: url(/bg-01.jpg);">
	<form action="https://www.google.co.jp/search" method="get">
		<input type="hidden" name="hl" value="ja" />
		<label class="input input-lg w-full md:w-xl">
			<svg class="h-[1em] opacity-50" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				<g
					stroke-linejoin="round"
					stroke-linecap="round"
					stroke-width="2.5"
					fill="none"
					stroke="currentColor"
				>
					<circle cx="11" cy="11" r="8"></circle>
					<path d="m21 21-4.3-4.3"></path>
				</g>
			</svg>
			<input type="search" name="q" maxLength="255" required placeholder="Search" />
		</label>
	</form>
</div>

{#each linkGroups as linkGroup}
	<div class="links-container">
		<h2 class="text-2xl py-4 bg-neutral-">{linkGroup.name}</h2>
		<div class="flex flex-wrap gap-4">
			{#each linkGroup.links as link}
				<div class="card bg-base-100 w-96 shadow-sm">
					<div class="card-body">
						<h2 class="card-title">{link.name}</h2>
						<p class="whitespace-pre-wrap">{link.description}</p>

						<div class="card-actions justify-between">
							<div>
								{#if link.network === 'vpn'}
									<div class="badge badge-accent">VPN</div>
								{:else if link.network === 'local'}
									<div class="badge badge-secondary">Local</div>
								{/if}
							</div>
							<a href={link.url} target="_blank" class="btn btn-primary">Go</a>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
{/each}

<style>
	#hero {
		background-size: cover;
		background-position: center;
		padding: 10rem 4rem;
		@media screen and (max-width: 640px) {
			padding: 5rem 1rem;
		}
		text-align: center;
	}

	.links-container {
		/* display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center; */
		padding: 1rem;
		margin-left: auto;
		margin-right: auto;
		max-width: 95%;
		/* padding: 4rem 2rem; */
	}
</style>
