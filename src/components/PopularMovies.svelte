<script>
	export let popular;
	import MovieCard from './MovieCard.svelte';
</script>

<h2>Popular Movies</h2>
<div class="popular-movies">
	{#each popular as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	h2 {
		padding: 0 1rem;
		font-size: 2rem;
		text-align: center;
		margin-bottom: 2rem;
	}
	.popular-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
		height: 30vh;
	}
</style>
