<template>
    <tr>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre"> <TextHighlight :queries="query">{{ meteorite.name }}</TextHighlight></td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre hidden sm:inline-block">{{ meteorite.id }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre hidden sm:inline-block">{{ meteorite.nametype }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre hidden sm:inline-block">{{ meteorite.recclass }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.mass }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre hidden sm:inline-block">{{ meteorite.fall }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre hidden sm:inline-block">{{ meteorite.year }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre hidden sm:inline-block">{{ typeof meteorite.geolocation !=='undefined' ?meteorite.geolocation.latitude:'' }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre hidden sm:inline-block">{{ typeof meteorite.geolocation !=='undefined' ?meteorite.geolocation.longitude:'' }}</td>
    </tr>
</template>
<script>
import TextHighlight from 'vue-text-highlight';

export default {
    name: 'Meteorite',
    props: {
        meteorite: Object
    },
    components:{
        TextHighlight
    },
    data: function(){
        return {
            query: ''
        }
    }
    ,
    mounted(){
        this.$root.$on('search', (q) => {
            this.query = q;           
         })
    }
}
</script>

