<template>
        <v-row
            v-masonry
            item-selector=".item">
            <v-col
                v-for="movie in movies"
                :key="movie.imdbID"
                cols="12"
                lg="3"
                md="4"
                sm="6"
                v-masonry-tile
                class="item">
                <v-card>
                    <v-img
                        :src="posterSrc(movie.Poster)"
                        :alt="movie.Title"
                        :height="posterHeight(movie.Poster)">
                            <template v-slot:placeholder>
                                <div style="background: lightgray; height: 100%;"></div>
                            </template>
                        </v-img>
                    <v-card-title>
                        {{ movie.Title }}
                    </v-card-title>
                    <v-card-subtitle>
                        {{ movie.Year }}
                    </v-card-subtitle>
                </v-card>
            </v-col>
        </v-row>
</template>
<script>
export default {
    computed: {
        movies () {
         return this.$store.state.movie.movies   
        }
    },
    methods: {
        posterSrc (poster) {
            return poster === 'N/A' ? '' : poster
        },
        posterHeight (poster) {
            return poster === 'N/A' ? 200 : 450
        }
    }
}
</script>