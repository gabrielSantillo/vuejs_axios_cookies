<template>
  <div>
    <button @click="handle_click">Cat Button</button>
  </div>
</template>

<script>
import axios from "axios";
import cookies from "vue-cookies";

export default {
   mounted() {
    let is_cat = cookies.get(`selection`);
    if (is_cat === `cat`) {
      this.handle_click();
    }
  },

  methods: {
    handle_click() {
      axios
        .request({
          url: `https://aws.random.cat/meow`,
        })
        .then((response) => {
          this.cat_img_url = response[`data`][`file`];
          this.$root.$emit(`new_display`, this.cat_img_url);cookies.set(`selection`, `cat`);
        })
        .catch((error) => {
          error;
        });
    },
  },
  data() {
    return {
      cat_img_url: undefined,
    };
  },
};
</script>

<style scoped>
button {
    margin-bottom: 50px;
}
</style>
