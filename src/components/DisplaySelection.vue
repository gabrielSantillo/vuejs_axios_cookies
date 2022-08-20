<template>
    <div v-if="img_received === true">
        <img :src="img_url" alt="">
    </div>
</template>

<script>
    export default {
        data() {
            return {
                img_url: undefined,
                img_received: false
            }
        },
        methods: {
            handle_img_url(message) {
                this.img_url = message;
                this.img_received = true
            }
        },
        mounted () {
            this.$root.$on(`new_display`, this.handle_img_url);
        },
    }
</script>

<style scoped>

</style>