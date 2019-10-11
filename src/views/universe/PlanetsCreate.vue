<template>
    <div>
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
                    <form>
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
                        <v-btn text @click="save">
                            Add planet
                        </v-btn>
                    </form>
                </v-card-text>
            </v-card>
        </v-flex>
    </v-layout>
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        mounted() {
            this.save()
        },
        data()  {
            return{
            universes:[],
            planetName: '',
            price: +'',
            population:+ '',
            gravity: '',
            size: '',
            mainResource: '',
            planetType:+ ''
        }},
        methods: {
            save() {
                axios.post('http://planetcrossdis.azurewebsites.net/api/planets'
                ,{
                    planetName: this.planetName,
                    price: +this.price,
                    population: +this.population,
                    gravity: this.gravity,
                    size: this.size,
                    mainResource: this.mainResource,
                    planetType: +this.planetType
                });
            }
        }
    };
</script>