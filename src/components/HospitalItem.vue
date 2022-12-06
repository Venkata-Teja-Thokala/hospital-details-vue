<template>
    <div class = 'card'>
        <div id="name">{{Hospital.name}}</div>
        <div class="container">
            <div class="innerContainer">
                <div class="details">
                    <p>Medicare Provider No : {{Hospital.medicare_provider_number}}</p>
                    <p>Bed Count : {{Hospital.hospital_bed_count}}</p>
                    <p>Children Hospital : {{Hospital.children_hospital_f}}</p>
                    <p>Urban Location : {{Hospital.urban_location_f}}</p>
                    <p>As of Date: {{Hospital.updated_dt}}</p>
                </div>
                <div class="address">
                    <p><b>Address : </b></p>
                    <p>{{Hospital.street_address}}</p>
                    <p>{{Hospital.city}}</p>
                    <p>{{Hospital.state}}</p>
                    <p>{{Hospital.zip_code}}</p>
                    <p>{{Hospital.county}}</p>
                </div>
            </div>    
        </div>
    </div>
</template>

<script>

export default {
    name : 'HospitalItem',
    props: {
        Hospital : Array
    }
}
</script>

<style scoped>
*{
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    box-sizing: border-box;
    padding: 0px;
    margin: 0px;
}



.card {
  display : block;
  box-shadow: 2px 2px 4px 2px rgba(0.2,0.2,0.2,0.2);
  transition: 0.3s;
  width: 450px;
  height: 200px;
  margin: 20px;
}

.details {
    padding: 10px;
    font-size: 17px;
    width: 70%;
    margin: 1px;
}

.details p {
    padding-bottom: 3px;
}

.innerContainer {
    display : inline-flex;
    width: 100%;
    height:160px;
}

.container {
  font-size: 10px;
  padding: 3px;
  background-image: linear-gradient(to bottom right, #CE9FFC, #7367F0);
  border: gray 1px;
}

.card:hover {
  box-shadow: 4px 4px 8px 4px rgba(0.4,0.4,0.4,0.4);
}

#name {
    text-align: center;
    font-weight: bold;
    color: black;
    font-size: 25px;
    height: 40px;
    padding:10px 5px 10px 5px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.address{
    padding: 7px;
    font-size: 13px;
    margin: 1px;
}



@media only screen and (max-width: 400px) {
    .card {
        width : 100vw;
    }
    
}
</style>
