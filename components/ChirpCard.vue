<template>
  <b-card no-body img-left>
    <b-row no-gutters>
      <b-col cols="2" md="3">
        <b-avatar
          :src="getImgUrl(chirp.thumbnail)"
          class="thumbnail"
          size="64px"
          variant="light"
        />
      </b-col>
      <b-col cols="10" md="9">
        <b-card-body :title="chirp.author">
          <b-card-text>
            {{ chirp.text }}
            <div class="chirpHashtags">
              <span v-for="hashtag in chirp.hashtags" :key="hashtag"
                >{{ hashtag }}
              </span>
            </div>
          </b-card-text>
        </b-card-body>
      </b-col>
    </b-row>
  </b-card>
</template>

<script>
export default {
  name: "ChirpCard",
  props: {
    chirp: {
      type: Object,
      required: true,
    },
  },
  methods: {
    getImgUrl(thumbnailPath) {
      return require("../assets/" + thumbnailPath);
    },
  },
};
</script>

<style scoped>
.thumbnail {
  margin: 6px 0px 0px 6px;
}
.chirpHashtags {
  color: cornflowerblue;
  margin-top: 6px;
  display: inline;
}
</style>