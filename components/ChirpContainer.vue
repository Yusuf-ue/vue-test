<template>
  <b-container>
    <b-row>
      <b-col cols="12" md="6" lg="4" v-for="chirp in chirps" :key="chirp.id">
        <chirp-card :chirp="chirp" class="chirpCard" />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import ChirpCard from "./ChirpCard.vue";

export default {
  name: "ChirpContainer",
  components: {
    ChirpCard,
  },
  props: {
    chirps: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
    .chirpCard {
    margin: 12px 0px 0px 0px;
    }
</style>