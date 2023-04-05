<template>
  <header>
    <div id="logo-div">
      <img src="../../public/images/logo.png" alt="logo" />
      <h2>VueTube</h2>
    </div>
    <div class="col-md-8">
      <div class="input-group flex-nowrap">
        <input
          type="text"
          class="form-control"
          placeholder="Pesquise aqui"
          aria-label="Pesquise aqui"
          aria-describedby="addon-wrapping"
          @keyup.enter="onInput"
        />
        <button class="btn btn-primary" @click="onInput">🔎</button>
      </div>
    </div>
    <div id="user-div">
      <img src="../../public/images/58229727.jpg" alt="user_picture" />
    </div>
  </header>
</template>
<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(event) {
      this.$emit("termChange", event.target.value);
    },
  },
};
</script>
<style scoped>
input {
  width: 75%;
}

header {
  display: flex;
  margin: 0;
  width: 100%;
  justify-content: space-around;
  align-items: center;
  padding: 20px;
}

header input {
  width: 50%;
}

#user-div {
  text-align: center;
}

#logo-div {
  display: flex;
  align-items: center;
}

#logo-div img,
#user-div img {
  max-width: 60px;
}

#user-div img {
  border-radius: 50%;
}
</style>
