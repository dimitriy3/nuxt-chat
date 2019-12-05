<template>
  <v-flex xs12>
    <v-text-field class="field" label="Введите сообщение" outline v-model="text" @keydown.enter="send"/>
    <v-btn icon @click="send" class="btn">
      <v-icon>send</v-icon>
    </v-btn>
  </v-flex>
</template>

<script>
export default {
  data: () => ({
    text: ""
  }),
  methods: {
    send() {
      this.$socket.emit(
        "createMessage",
        {
          text: this.text,
          id: this.$store.state.user.id
        },
        data => {
          if (typeof data === "string") {
            console.error(data);
          } else {
            this.text = "";
          }
        }
      );
    }
  }
};
</script>

<style scoped>

.btn {
  z-index: 99999;
  position: absolute;
  bottom: 10px;
  right: 15px;
}

</style>
