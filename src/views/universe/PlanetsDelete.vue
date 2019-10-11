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
                        Delete Planet/Star/Moon
                    </v-card-title>
                    <v-card-text>
                        <form>
                            <v-text-field
                                    v-model="id"
                                    label="Id"
                                    required
                            />
                            <v-btn text @click="deletePlanet">
                                Delete planet
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
        },
        data()  {
            return{
                universes:[],
                id: +'',

            }},
        methods: {
            async deletePlanet(universe) {
                let result = await axios.delete('http://planetcrossdis.azurewebsites.net/api/planets/' +this.id)
                if(result.status !== 200) {
                    // this.universes.push(universe)
                } else {
                    this.fetch()
                }
            }
        }
    };
</script>