<template>
	<div>
		<div class="grid">
			<movie v-for="movie in movies" :key="movie.id" :title="movie.title" :image="'https://image.tmdb.org/t/p/w500/' + movie.poster_path" :rating="movie.vote_average" />
		</div>
		<div class="pagination">
			<!-- 1. Add logic to these pagination links so they appear on the page correctly. -->
			<!-- 2. Add click events that update the page variable. -->
			<!-- [First] [3] [4] [5] [Last] -->
			<a href="#movies" class="yess"> First </a>
			<a href="#movies" class="current">{{ page }}</a>
			<a href="#movies">{{ page + 1 }}</a>
			<a href="#movies">{{ page + 2 }}</a>

			<a href="#movies">{{ page + 3 }}</a>
			<a href="#movies">{{ page + 4 }}</a>
			<a href="#movies" class="yess"> Last </a>
		</div>
	</div>
</template>

<script>
import Movie from './Movie';
import axios from 'axios';
export default {
	components: { Movie },

	props: ['genre'],

	data() {
		return {
			page: 1,
			movies: [],
			totalPages: 500
		}
	},

	// Call the API on startup.
	mounted() {
		this.callAPI();
	},

	// Anytime the genre or page variable is updated, call the API.
	watch: {
		genre() {
			this.page = 1;
			this.callAPI();
		},
		page() {
			this.callAPI();
		}
	},

	methods: {
		callAPI() {
		getResult(movies){
		axios.get('https://api.themoviedb.org/3/movie/550?   api_key=753cbe6c1ec161e02cacd1e323a83454' + movie).then(response => { this.results = response.data.results})
		 	console.log(this.results)
}
}
}			// 1. Make an ajax request to TMDb with the correct page and genre.
			// 2. Update the following variables: movies, totalPages.

			//
			// xhttp.open("GET", "")
			//
		}
	}

}
</script>
