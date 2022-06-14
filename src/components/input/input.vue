<script>
import { defineComponent } from 'vue'
import jsonSport from '../Data/data.json'

export default defineComponent({
    data(){
        return{
            sports: jsonSport,
            inputSport: null,
            resultFound: null
        }
    },
    methods:{
        resultJsonSport(){
            console.log(this.resultFound);
            let searchInput = this.inputSport.toLowerCase();
            let filterArray = this.sports.Sport.filter(item => item.name.toLowerCase().includes(searchInput))
            this.resultFound = filterArray;  
            console.log(this.resultFound);
        }
    },
    beforeUpdate(){
        this.resultJsonSport();
    }
})
</script>

<template>
    <div>
        <h1>{{inputSport}}</h1>
        <input type="text" v-model="inputSport">
    </div>
    <div v-if="resultFound == null">
        <div v-for="(sport , id) in sports.Sport" v-bind:key="id">
            {{sport.name}}
        </div>
    </div>
    <div v-for="(sports , id) in resultFound" v-bind:key="id">
        {{sports.name}}
    </div>
</template>

<style>

</style>