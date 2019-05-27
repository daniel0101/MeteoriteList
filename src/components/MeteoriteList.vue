<template>
    <div class="sm:m-16 ml-3 mt-10">
        <Loader v-if="loading" />
        <table v-else class="w-full text-left table-auto table-collapse">
            <tr>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100">Name</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100 hidden sm:table-cell">Id</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100 hidden sm:table-cell">Name Type</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100 hidden sm:table-cell">Rec Class</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100">Mass(g)</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100 hidden sm:table-cell">Fall</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100 hidden sm:table-cell">Year</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100 hidden sm:table-cell">Latitude</th>
                <th class="text-sm font-semibold text-gray-700 p-2 bg-gray-100 hidden sm:table-cell">Longitude</th>
            </tr>
            <tbody>
                <div v-if="isEmpty" class="mt-3">
                    <p class="text-lg font-bold">No content(s) found for <span class="text-blue-500">{{query}}</span></p>
                </div>                
                <Meteorite v-else v-for="list in lists" :key="list.id" :meteorite="list"> </Meteorite>
            </tbody>
        </table>
    </div>
</template>
<script>
import axios from 'axios';
import Meteorite from './Meteorite.vue';
import Loader from './Loading.vue';
export default {
    name: 'List',
    components:{
        Meteorite,
        Loader
    },
    data: function(){       
        return {
            lists: [],
            allLists: [],
            query:'',
            loading: true,
            isEmpty: false
        }
    },
    mounted: function (){
        axios.get('https://data.nasa.gov/resource/gh4g-9sfh.json')
        .then(response =>{
            this.loading = false;
            response.data.forEach((meteorite)=>{
                var date = new Date(meteorite.year);
                meteorite.year = date.getFullYear();
            })
            this.lists = response.data;
            this.allLists = response.data;
        })
        .catch(err => alert('Could not fetch Meteorite Data due to '+err));

        //listen for the search event here --from the Search component
        this.$root.$on('search', (query) => {
            //set query to local data
            this.query = query;

            this.isEmpty = false;
            // alert(query);
            //convert query to small letter
            query = query.toLowerCase();
            //filter search query in result
            this.lists = this.allLists.filter((meteorite)=>{
                return meteorite.name.toLowerCase().indexOf(query) != -1
            });

            if(this.lists.length ===0){
                this.isEmpty = true;
            }           
         })
    },
    methods: {
       
    }
}
</script>

