<template>
	<div>
		<div class="grid">
			<movie v-for="movie in movies" :key="movie.id" :title="movie.title" :image="'https://image.tmdb.org/t/p/w500/' + movie.poster_path" :rating="movie.vote_average" />
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
		this.fetchData();
	},

	// Anytime the genre or page variable is updated, call the API.
	watch: {
		genre() {
			this.page = 1;
			this.fetchData();
		},
		page() {
			this.fetchData();
		}
	},
	created: function() {
			// Create the method you made below
			this.fetchData();
	},
	methods: {
			// Fetch data from the API
			fetchData: function() {
					axios.get(`https://api.themoviedb.org/3/discover/movie?api_key=753cbe6c1ec161e02cacd1e323a83454&with_genres=${this.genre}`).then(response => {
							this.movies = response.data.results;
							this.loaded = false;
					});
			}
	}
}

</script>
