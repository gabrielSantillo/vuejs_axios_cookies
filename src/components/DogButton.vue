<template>
  <div>
    <button @click="setting_dog_cookie">Dog Button</button>
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
        })
        .catch((error) => {
          error;
        });
    }
  },

  methods: {
    setting_dog_cookie() {
      cookies.set(`selection`, `dog`);
      axios
        .request({
          url: `https://dog.ceo/api/breeds/image/random`,
        })
        .then((response) => {
          this.dog_img_url = response[`data`][`message`];
          this.$root.$emit(`new_display`, this.dog_img_url);
        })
        .catch((error) => {
          error;
        });
    },
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
