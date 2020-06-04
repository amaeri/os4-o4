<script>
	
	let steder = []
	let sted = ""
	
	async function searchStops() {
		const response = await fetch("https://api.entur.io/geocoder/v1/autocomplete?text=" + sted + "&lang=en")
		const json = await response.json()
		console.log(json)
		steder = json.features
	}
	
	searchStops();
</script>

<main>
	<section>
		<div>
			<h1>Oppgave 4</h1>
			<p>Supernøtt: Se på filmen med ekstrastoff i leksjonen for Dag 4 hvor jeg henter ut en noen tilfeldige folk. Se om du kan bruke den samme teknikken til å hente ut info om noe annet. Det fins mange forskjellige datakilder der ute.</p>
		</div>
		
		<h3>Hvor vil du reise?</h3>
		<p>Søk på destinasjon:</p>
		<input bind:value={sted} on:input={searchStops}>
		
		<article>
		{#each steder as sted}
			<p>{sted.properties.label}</p>
		{/each}
		</article>
	</section>
</main>

<style>
	main {
		display: grid;
		place-items: center;
		padding: 1rem;
		font-family: 'Poppins';
	}	

	section {
		width: 70%;
		background-color: #003F6E;
		color: white;
		padding: 1rem;
	}

	div {
		border-bottom: 1px white solid;
	}

	h3 {
		text-transform: uppercase;
	}
	
</style>