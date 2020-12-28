<template>
  <v-card role="button">
    <v-hover v-slot="{ hover }">
      <v-img :aspect-ratio="0.6" :src="movie.poster">
        <template v-slot:placeholder>
          <v-row
              align="center"
              class="fill-height ma-0"
              justify="center"
          >
            <v-progress-circular
                color="grey lighten-5"
                indeterminate
            ></v-progress-circular>
          </v-row>
        </template>
        <v-row align="end" class="fill-height">
          <div class="overlay mb-n3 px-6">
            <v-expand-transition>
              <div v-if="hover">
                <h3 class="text-body1">{{movie.title}}</h3>
              </div>
            </v-expand-transition>

            <VRating
                :value="movie.rating/10*5"
                background-color="white"
                class="mx-n3"
                color="yellow darken-3"
                half-increments
                readonly
                small
            />
          </div>
        </v-row>
      </v-img>
    </v-hover>
  </v-card>
</template>

<script>
export default {
  name: 'MoviePoster',
  props: {
    movie: {
      required: true,
      type: Object,
    }
  }
};
</script>


<style scoped>
.v-card {
  width: 160px;
}
.overlay {
  background: rgba(0, 0, 0, 0.4);
}
</style>
