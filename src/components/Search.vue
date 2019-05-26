<template>
    <div>
        <input type="text" class="w-8/12 sm:w-5/12 p-2 rounded border-none shadow-lg" v-model="query" v-on:keyup="search" placeholder="Search Meteorite Landings">
        <!-- <button class="bg-blue-500 p-2 shadow-lg rounded-r text-white" v-on:click="search">Search</button> -->
    </div>
</template>
<script>
export default {
    name: 'Search',
    data: function(){
        return {
            query: ''
        }
    },
    methods:{
        search(){
            this.$root.$emit('search',this.query);
        }
    }
}
</script>

