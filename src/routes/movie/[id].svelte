<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=${
				import.meta.env.VITE_API_KEY
			}&language=en-US`
		);
		const movieDetail = await res.json();

		if (res.ok) {
			return {
				props: { movieDetail }
			};
		}
	}
</script>

<script>
	export let movieDetail;
	import { fly } from 'svelte/transition';
</script>

<div
	class="movie-details"
	in:fly={{ y: 50, duration: 500, delay: 500 }}
	out:fly={{ duration: 500 }}
>
	<div class="img-container">
		<img
			src={'https://image.tmdb.org/t/p/original' + movieDetail.poster_path}
			alt={movieDetail.title}
		/>
	</div>
	<div class="text-container">
		<h2>{movieDetail.title}</h2>
		<p class="overview">{movieDetail.overview}</p>
		<p>
			<span>Release Date: </span>{movieDetail.release_date}
			<br />
			<span>Budget: </span>{movieDetail.budget}
			<br />
			<span>Raiting: </span>{movieDetail.vote_average}
			<br />
			<span>Runtime: </span>{movieDetail.runtime} mins
		</p>
	</div>
</div>

<style>
	h2 {
		padding: 1rem 0 2rem;
	}
	p {
		padding: 1rem 0;
	}
	.img-container {
		width: 100%;
	}
	img {
		width: 100%;
		border-radius: 1rem;
	}
	.movie-details {
		margin: 2rem 20%;
	}
	span {
		font-weight: bold;
	}
</style>
