<script>
	let merchantData;
	let fetchLoading = true;
	import { onMount } from 'svelte';
	import Header from './components/Header.svelte'
	import Restorant from './components/Restorant.svelte';
	import Spinner from 'svelte-spinner';
		
	onMount(()=>{
		if(navigator.geolocation){
			const showPosition =async (position) => {
				const latitude = position.coords.latitude;
				const longitude = position.coords.longitude;
				const result = await fetch(`https://asia-east2-fooddiscovery-ab508.cloudfunctions.net/nearbyFoodPromotions?lat=${latitude}&long=${longitude}`);
				const parse = await result.json();
				merchantData = parse;
				fetchLoading = false;
			}
			const showError = (err) => {
				console.log(err)
			}
			navigator.geolocation.getCurrentPosition(showPosition,showError)
		}
	})
</script>

<style>
	.loader-wrapper {
		width: 100%;
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>

<main>
	<Header />
		{#if !fetchLoading}
			{#each merchantData.searchResult.searchMerchants as { address, merchantBrief } }
				<Restorant 
					restorantName={address.name} 
					restorantRating={merchantBrief.rating}
					restorantType={merchantBrief.cuisine.join(', ')}
					restorantImage={merchantBrief.photoHref}
					restorantDistance={Number(merchantBrief.distanceInKm).toFixed(2)}
				/>
			{/each}
		{/if}
		{#if fetchLoading}
			<div class="loader-wrapper">
				<Spinner
					size="50"
					speed="750"
					color="#A82124"
					thickness="2"
					gap="40"
				/>
			</div>
		{/if}
</main>