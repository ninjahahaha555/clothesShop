<template>
    <v-app>
        <v-carousel>
            <v-carousel-item
            v-for="(item,i) in items"
            :key="i"
            :src="item.src"
            reverse-transition="fade-transition"
            transition="fade-transition"
            ></v-carousel-item>
        </v-carousel>
        <v-container fluid>
            <v-row dense>
                <v-col
                v-for="product in products"
                :key="product.id"
                :cols="3"
                >
                <v-card>
                    <v-img
                    class="white--text align-end"
                    gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                    height="200px"
                    >
                    <v-card-title v-text="product.name"></v-card-title>
                    </v-img>

                    <v-card-actions>
                    <v-spacer></v-spacer>

                    <v-btn icon>
                        <v-icon>mdi-heart</v-icon>
                    </v-btn>

                    <v-btn icon>
                        <v-icon>mdi-bookmark</v-icon>
                    </v-btn>

                    <v-btn icon>
                        <v-icon>mdi-share-variant</v-icon>
                    </v-btn>
                    </v-card-actions>
                </v-card>
                </v-col>
            </v-row>
        </v-container>
    </v-app>
</template>

<script>
    export default {
        data() {
            return {
                products: [],
                product: null,
                items: [
                    {
                        src: 'https://cdn.discordapp.com/attachments/841250203985248276/955189974838419486/man5.jpg',
                    },
                    {
                        src: 'https://cdn.discordapp.com/attachments/841250203985248276/955190442645925978/man6.jpg',
                    },
                    {
                        src: 'https://cdn.discordapp.com/attachments/392289289750315008/955188017943941220/2000.jpg',
                    },
                ],
            }
        },
        mounted() {
            this.initialize()
            console.log('Initialized')
        },
        methods:{
            initialize(){
                axios.get('api/product')
                    .then(response => {
                        if(response.data.success == true){
                            this.products = response.data.products
                        }
                    })
                    .catch(error => {
                        console.log("error")
                    });
            },
        },
    }
</script>
