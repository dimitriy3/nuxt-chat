<template>
  <div>
    <div v-if="name === 'admin'" class="system">
      <p class="text-xs-center">{{text}}</p>
      <hr>
    </div>
    <div v-else class="wrap">
      <div class="mes" :class="{owner}">
        <small>
          <strong>{{name}}</strong>
        </small>
        <p>{{text}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    text: String,
    owner: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style lang="stylus" scoped>

.system {
  margin-bottom: 1rem;

  p {
    margin-bottom: 1rem;
  }
}

.wrap {
  display: flex;
  flex-direction: column;
}

.mes {
  padding: 10px 15px;
  width: 40%;
  margin: 0 1rem;
  box-shadow: 0 1px 0 0 rgba(50, 50, 50, 0.3);
  border-radius: 14px;
  background: #e2e2e2;
  position: relative;
  color: black;
  margin-bottom: 1rem;

  p {
    margin-bottom: 0;
  }
}

.owner {
  background: #1976d2;
  color: #ffffff;
  align-self: flex-end;
}

@media screen and (max-width: 400px) {
  .mes {
    width: 60%;
    padding: 5px 10px;
  }
}

</style>

