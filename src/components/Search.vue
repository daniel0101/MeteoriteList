<template>
    <div>
        <input type="text" class="w-4/12 p-2 rounded-l border-none shadow-lg" v-model="query" v-on:keyup="search">
        <button class="bg-blue-500 p-2 shadow-lg rounded-r text-white" v-on:click="search">Search</button>
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

