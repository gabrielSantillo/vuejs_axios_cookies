<template>
  <div>
    <button @click="random_img_dog">Dog Button</button>
  </div>
</template>

<script>
import axios from "axios";
import cookies from "vue-cookies";

export default {
  mounted() {
    let is_dog = cookies.get(`selection`);
    if (is_dog === `dog`) {
      axios
        .request({
          url: `https://dog.ceo/api/breeds/image/random`,
        })
        .then((response) => {
          this.dog_img_url = response[`data`][`message`];
          this.$root.$emit(`new_display`, this.dog_img_url);
          cookies.set(`selection`, `dog`);
        })
        .catch((error) => {
          error;
        });
    }
  },

  data() {
    return {
      dog_img_url: undefined,
    };
  },
};
</script>

<style scoped>
button {
  margin-bottom: 50px;
}
</style>
