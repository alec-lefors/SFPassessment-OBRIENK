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
created: function() {
		// Create the method you made below
		this.fetchData();
},
methods: {
		// Fetch data from the API
		fetchData: function() {
				this.$http.get(this.baseUrl + '/discover/movie?api_key=' + this.apiKey + '&sort_by=popularity.desc').then(response => {
						this.items = response.body;
						this.loaded = false;
				});
		}
}


</script>
