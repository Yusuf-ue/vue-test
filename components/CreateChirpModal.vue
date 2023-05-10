<template>
  <div>
    <b-button v-b-modal.modal-1 size="sm" variant="outline-light">Chirpen!</b-button>
    <b-modal id="modal-1" title="Neuen Chirp erstellen" @ok="addChirp">
		
      <b-form-group id="author" label="Dein Name *" label-for="input-author">
        <b-form-input id="input-author" v-model="newChirp.author" trim />
      </b-form-group>

      <b-form-group
        id="description"
        label="Deine Nachricht *"
        label-for="input-author"
        :description="'Noch ' + remainingCharacters + ' Zeichen übrig'">
        <b-form-textarea
          id="textarea-message"
          placeholder="max. 200 Zeichen"
          rows="3"
          max-rows="6"
          maxlength="200"
          v-model="newChirp.text" />
      </b-form-group>

      <b-form-group
        id="description"
        label="Hashtags:"
        label-for="input-author"
        description="Hashtags durch Leerzeichen getrennt angeben">
        <b-form-input
          id="input-hashtags"
          placeholder="z.B. #hashtag1 #hashtag2"
          v-model="hashtagString" />
      </b-form-group>
    </b-modal>
  </div>
</template>

<script>
export default {
  name: "CreateChirpModal",
  data() {
    return {
      hashtagString: "",
      newChirp: {
        author: "",
        text: "",
        hashtags: [],
      },
    };
  },
  computed: {
    remainingCharacters: function () {
      return 200 - this.newChirp.text.length;
    },
  },
  methods: {
    addChirp(bvModalEvt) {
      if (this.newChirp.author && this.newChirp.text) {
        this.newChirp.hashtags = this.hashtagString
          .split(" ")
          .map((h) => "#" + h.replace("#", ""));
        this.$emit("added-chirp", this.newChirp);
        return;
      } else {
        bvModalEvt.preventDefault();
        return;
      }
    },
  },
};
</script>

<style scoped>
</style>