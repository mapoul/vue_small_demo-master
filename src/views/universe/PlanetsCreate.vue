<template>
    <v-layout
            column
            justify-center
            align-right
    >
        <v-flex
                xs12
                sm8
                md6
        >
            <v-card width="400px">
                <v-card-title class="headline">
                    Create Planet/Star/Moon
                </v-card-title>
                <v-card-text>
                    <form @submit.prevent="addArticle">
                        <v-text-field
                                v-model="planetName"
                                label="Planet Name"
                                required
                        />
                        <v-text-field
                                v-model="price"
                                label="Price"
                                required
                        />
                        <v-text-field
                                v-model="population"
                                label="Population"
                                required
                        />
                        <v-text-field
                                v-model="gravity"
                                label="Gravity Compared to Earth"
                                required
                        />
                        <v-text-field
                                v-model="size"
                                label="Size compared to Earth"
                                required
                        />
                        <v-text-field
                                v-model="mainResource"
                                label="Main Resource"
                                required
                        />
                        <v-text-field
                                v-model="planetType"
                                label="Planet type (in numbers)"
                                required
                        />
                        <v-btn text v-on:click="save()">
                            Add planet
                        </v-btn>
                    </form>
                </v-card-text>
            </v-card>
        </v-flex>
    </v-layout>
</template>
<script>
    export default {
        data:() => ({
            planetName: '',
            price: '',
            population: '',
            gravity: '',
            size: '',
            mainResource: '',
            planetType: ''
        }),
        methods: {
            /**
             * [addArticle used to Add Article]
             */
            save() {
                const baseURI = 'http://planetcrossdis.azurewebsites.net/api/planets';
                axios.post(baseURI,{
                    planetName: this.planetName,
                    price: this.price,
                    population: this.population,
                    gravity: this.gravity,
                    size: this.size,
                    mainResource: this.mainResource,
                    planetType: this.planetType
                })
                    .then((result) => {console.log(result)})
            }
        }
    }
</script>