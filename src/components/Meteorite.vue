<template>
    <tr>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.name }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.id }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.nametype }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.recclass }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.mass }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.fall }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ meteorite.year }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ typeof meteorite.geolocation !=='undefined' ?meteorite.geolocation.latitude:'' }}</td>
        <td class="p-2 border-t border-gray-300 font-mono text-xs whitespace-pre">{{ typeof meteorite.geolocation !=='undefined' ?meteorite.geolocation.longitude:'' }}</td>
    </tr>
</template>
<script>
export default {
    name: 'Meteorite',
    props: {
        meteorite: Object
    }
}
</script>

