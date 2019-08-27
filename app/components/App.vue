<template>
    <Page>
    <ActionBar title="Movie Factory"/>
      <Stacklayout>
        <TabView fontWeight="Bold" height="300px">
          <TabViewItem title="Popular">
            <ListView for="movie in movies">
              <v-template>
                <GridLayout
                    columns="90,*"
                    class="movie">
                        <Image
                            verticalAlignment="top"
                            class="movie-image"
                            :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" />
                        <StackLayout
                            col="1"
                            class="movie-details">
                                <GridLayout
                                    columns="*,50">
                                        <Label
                                            :text="movie.title"
                                            class="movie-title"
                                            textWrap="true" />
                                        <Label
                                            col="1"
                                            :text="movie.vote_average"
                                            class="movie-score"
                                            :class="getScoreClass(movie.vote_average)"/>
                                </GridLayout>
                                <Label
                                    :text="movie.overview"
                                    class="movie-overview"
                                    textWrap="true" />
                                <Button
                                    text="View Movie"
                                    class="view-movie-button"
                                    @tap="viewMovie(movie.id)" />
                        </StackLayout>
                </GridLayout>
              </v-template>
            </ListView>
          </TabViewItem>
        <TabViewItem title="Search">
          <Label fontWeight="Bold" fontSize="20" textAlignment="center" text="search" />
        </TabViewItem>
          <TabViewItem title="Settings">
            <Label fontWeight="Bold" fontSize="20" textAlignment="center" text="settings" />
          </TabViewItem>
          </TabView>
      </Stacklayout>
    </Page>
</template>

<script>
  import * as http from "http";
  import * as utils from 'tns-core-modules/utils/utils';

  export default {
    data() {
      return {
        myKey: "ea9385095138c0c18e3aca7590507b54",
        movies: [],
        msg: 'Hello World 2!'
      }
    },
    methods: {
      getAPIData() {
        http.getJSON("https://api.themoviedb.org/3/movie/popular?api_key="+this.myKey+"language=en-US&page=1")
        .then(result => {
          console.log("API");
          this.movies = result.results;
        }, error => {
          console.log(error);
        });
      },
      viewMovie(id) {
          utils.openUrl('https://www.themoviedb.org/movie/'+id);
      },
      getScoreClass(score) {
          return score > 8 ? 'green' : 'red';
      }
    },
    mounted() {
      this.getAPIData();
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #2274A5;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
    .movie-image {
        padding: 5;
        width: 80;
        height: 120;
    }
    .movie-title {
        font-weight: bold;
        padding: 5;
    }
    .movie-overview {
        padding: 5;
    }
    .movie-score {
        font-weight:bold;
        padding: 5;
    }
    .view-movie-button {
        background-color: green;
        color: white;
        font-weight: bold;
    }
    .green {
        color:green;
    }
    .red {
        color:red;
    }
</style>
