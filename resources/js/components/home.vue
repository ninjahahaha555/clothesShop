<style>
body {
    background-color: gray;
}
</style>
<template>
    <v-app style="background-color: gray">
        <v-row align="center" justify="space-around">
            <v-btn style="background-color: gray">
                <v-img
                    @click="redirect('/product')"
                    src="https://cdn.discordapp.com/attachments/841250203985248276/956629344678199326/03.jpg"
                ></v-img>
            </v-btn>
        </v-row>
    </v-app>
</template>

<script>
export default {
    data() {
        return {};
    },
    mounted() {
        this.initialize();
        console.log("Initialized");
    },
    methods: {
        redirect(url) {
            window.location.href = url;
        },
        initialize() {},
    },
};
</script>
