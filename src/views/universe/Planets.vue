<template>
    <div id="app">
        <ul>
            <li v-for="universe in universes" v-bind:key="universe.Id" >{{universe}}</li>
        </ul>
        <v-snackbar
                v-model="deletedSuccess">
            {{ deletedText }}
            <v-btn
                    color="pink"
                    text
                    @click="deletedSuccess = false"
            >Close</v-btn>
        </v-snackbar>
    </div>

</template>

<script>
    import axios from "axios";
    export default {
        name: "App",
        data(){
            return{
                IsLoading: false,
                universes: [],
                deletedSuccess: false,
                deletedText: 'Planet deleted'
            };
        },
        created(){
            this.fetch()
        },
        methods: {
            fetch () {
                this.IsLoading = true
                axios.get('http://planetcrossdis.azurewebsites.net/api/planets')
                    .then((response) => {
                        this.universes = response.data;
                        this.IsLoading = false
                    })

            },
            async deletePlanet(universe) {
                let result = await axios.delete('univers/' + universe.id)
                this.deletedSuccess = true;
                if(result.status !== 200) {
                    // this.albums.push(album)
                } else {
                    this.fetch()
                }
        },
    },
    }

</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>