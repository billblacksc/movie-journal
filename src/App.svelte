<script>
 import MovieInput  from './MovieInput.svelte';
 import MovieList  from './MovieList.svelte';
 
 

 let movies = localStorage.getItem('movies')?
	JSON.parse(localStorage.getItem('movies')):
	[];

 const submitMovie = movie => {
	 const updatedMovies = [ ...movies, movie ];
	 localStorage.setItem('movies',JSON.stringify(updatedMovies));
	 movies = updatedMovies;
	
 }
</script>

<div class='main'>
	<h1>Movie Journal</h1>

	<MovieInput on:submitMovie={event => submitMovie(event.detail.movie)} />
	<MovieList movies={movies} />

</div>

<style>
	.main{

	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	
</style>