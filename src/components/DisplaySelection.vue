<template>
    <div v-if="img_url !== undefined">
        <img :src="img_url" alt="">
    </div>
</template>

<script>
    export default {
        data() {
            return {
                img_url: undefined,
            }
        },
        methods: {
            handle_img_url(message) {
                this.img_url = message;
            }
        },
        mounted () {
            this.$root.$on(`new_display`, this.handle_img_url);
        },
    }
</script>

<style scoped>
img {
    max-width: 300px;
    max-height: 300px;
}
</style>