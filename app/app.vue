<template>
    <div style="height:100vh; width:100vw">
        <LMap
         :zoom="11" 
         :center="petropavl" 
         :use-global-leaflet="false"
         style="height: 100%; width: 100%">
            <LTileLayer
            url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
            attribution="&copy; OpenStreetMap contributors"
            />
            
            <LMarker :lat-lng="petropavl" :draggable="false">
                <LTooltip permanent direction="top">Petropavlovsk (NKR)</LTooltip>
                <LPopup>Petropavlovsk, North Kazakhstan region</LPopup>
            </LMarker>

        <LMarker
            v-for="(lake, i) in lakes"
            :key="i"
            :lat-lng="[lake.lat, lake.lng]"
            :draggable="false"
            >
        <LTooltip permanent direction="top">{{ lake.name }}</LTooltip>
    <LPopup>
        <strong>{{ lake.name }}</strong><br />
        Coordinates: {{ lake.lat }}, {{ lake.lng }}
    </LPopup>    
    </LMarker>
    </LMap>

    </div>
</template>



<script setup lang="ts">

import { ref } from 'vue'
import { LMap, LTileLayer, LMarker, LTooltip, LPopup } from '@vue-leaflet/vue-leaflet'
import 'leaflet/dist/leaflet.css'

type LatLngTuple = [Number, Number]

interface Lake {
    name: String
    lat: number
    lng: Number
}

const petropavl = ref<LatLngTuple>([54.88, 69.16])

const lakes = ref<Lake[]>([
    {name: 'lake Motley', lat: 54.836699, lng: 69.111328},
    {name: 'lake Beloe', lat: 54.927154, lng: 69.254322},
    {name: 'Lake gorky', lat: 54.947573, lng: 68.951122},
    {name: 'lake Grebe', lat: 54.921205, lng: 69.053476},
    {name: 'lake Wild', lat: 54.840156, lng: 69.131957},
    {name: 'lake Maloe Beloe', lat: 54.950605, lng: 69.326591},
    {name: 'lake Salty', lat: 54.809881, lng: 69.138257},
    {name: 'Bolshoe Tinnoe lake', lat: 54.803995, lng: 69.154565},
    {name: 'Porohovoe lake', lat: 54.802744, lng: 69.036282},
    {name: 'Cherepkovo lake', lat: 54.979913, lng: 69.355409},
    {name: 'Gusinoe lake', lat: 54.792959, lng: 69.137574},
    {name: 'Kishtibish 3rd lake', lat: 54.953839, lng: 69.178826},
    {name: 'Karabalka', lat: 54.961693, lng: 69.361721},
    {name: 'Pen`kovskoe lake', lat: 54.964191, lng: 69.261347},
    {name: 'Lebyazhe lake', lat: 55.153350, lng: 69.200989},
    {name: 'Rybnoe lake', lat: 54.886493, lng: 69.372847},
    {name: 'Baykal lake', lat: 55.038576, lng: 69.082739},
    {name: 'Safonkovo lake', lat: 55.026519, lng: 69.241075},
    {name: 'Chyornaya lake', lat: 54.812247, lng: 69.057172},
])
</script>


<!-- {name: '', lat: , lng: }, -->