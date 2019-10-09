<template>
    <div id="app">
        <ul>
            <li v-for="univers in universes" v-bind:key="univers.Id" >{{univers}}</li>
        </ul>

        <v-btn
                color="pink"
                text
                @click="deletedSuccess = false"
        >Delete</v-btn>
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
        },
    };

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