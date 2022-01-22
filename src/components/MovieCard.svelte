<script>
	export let movie;
</script>

<a class="link" sveltekit:noscroll sveltekit:prefetch href={'/movie/' + movie.id}>
	<div class="movie-card">
		<img src={'https://image.tmdb.org/t/p/w500' + movie.poster_path} alt={movie.title} />
		<div class="description">
			<h2>{movie.title}</h2>
			<p>{movie.release_date}</p>
		</div>
	</div>
</a>

<style>
	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		border-radius: 1rem;
		margin-bottom: 1rem;
	}
	h2 {
		font-size: 1rem;
	}
	.description {
		height: 5vh;
	}
	p {
		font-size: 0.8rem;
	}
	.movie-card {
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		padding: 1rem;
		height: 90%;
	}
	.link {
		color: #000;
		text-decoration: none;
	}
</style>
