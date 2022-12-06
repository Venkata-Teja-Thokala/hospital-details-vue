<template>
    <div class = "hContainer">
    <div v-for="Hospital in hospitals" :key="Hospital.hospital_id">
        <HospitalItem :Hospital="Hospital"></HospitalItem>
    </div>
    </div>
</template>

<script>
import HospitalItem from './HospitalItem.vue';

    export default {
        name : 'HospitalBox',
        props:{
            hospitals:Array
        },
        components:{
            HospitalItem
        } 
    }
</script>

<style scoped>
*{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: auto;
}

@media only screen and (max-width: 1300px) {
    * {
        grid-template-columns: 1fr 1fr;
    }
    
}

@media only screen and (max-width: 800px) {
    * {
        grid-template-columns: 1fr;
    }
    
}
</style>
