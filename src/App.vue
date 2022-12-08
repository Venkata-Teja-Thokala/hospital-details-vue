<template>
  <div>
    <div id="welcome">Welcome to Hospital Details</div>
    <div class="menu">
        <div class = "author">
          <AuthorDetails :name = "name"></AuthorDetails>
        </div>
        <div class="empty"></div>
        <div class="searchItems">
            <p id="errorMessage">{{errorMessage}}</p>
            <div><input v-model="stateCode" placeholder="State Code. ex: CT" />
            <button @click="doValidation">Search Hospitals</button>
            </div> 
        </div> 
    </div>
    <HospitalBox :hospitals="hospitals"/>
  </div>

</template>

<script>
import HospitalBox from './components/HospitalBox.vue';
import AuthorDetails from './components/AuthorDetails.vue';
import axios from 'axios';

  export default {
    name: "App",
    components:{
      HospitalBox,
      AuthorDetails
    },
    data() {
      return {
        hospitals: [],
        stateCode : 'CT',
        errorMessage:''
      }
    },
    methods: {
       async fetchHospitals(stateCodeVal) {
        if(!stateCodeVal){
          this.stateCode = stateCodeVal;
        }
        const res =   await axios.get('https://hospital-details-by-us-state-tvt.cyclic.app/hospitalDetails?state='+this.stateCode, {
          mode:'no-cors',
          referrerPolicy: 'origin'
        });
        const response =  res.data;
        if(this.stateCode != 'CT') {
          this.$forceUpdate();
        }
        return response;
      },

      async doValidation() {
            const stateCodes = ["AL","AK","AZ","AR","CA","CO","CT","DE","DC",
                                "FL","GA","HI","ID","IL","IN","IA","KS","KY",
                                "LA","ME","MD","MA","MI","MN","MS","MO","MT",
                                "NE","NV","NH","NJ","NM","NY","NC","ND","OH",
                                "OK","OR","PA","PR","RI","SC","SD","TN","TX",
                                "UT","VT","VA","WA","WV","WI","WY"];
            if(!stateCodes.includes(this.stateCode)) {
                this.errorMessage = "Not a valid state code. Just two words. Example: For Connecticut its CT";
            } else {
                this.errorMessage ='';
                console.log(this.stateCode);
                this.hospitals = await this.fetchHospitals(this.stateCode);
            }
        },
        async getAboutMe() {
          await axios.get('https://outstanding-pear-bullfrog.cyclic.app/about', {
          mode:'no-cors',
          referrerPolicy : 'origin',
        });
        }
    },

    async created() {
      this.hospitals = await this.fetchHospitals(this.stateCode);
    }
  }
</script>

<style scoped>
* {
  padding: 0px;
  margin:0px;
  box-sizing:border-box;
}
#welcome{
  text-align: center;
  color: white;
  background-color: blueviolet;
  font-size: 30px;
  height: 50px;
  padding-top: 7px;
  
}
.empty{
  width:50%;
}
.menu {
    width: 100%;
    height: 40px;
    margin-top: 10px;
    display: inline-flex;
    border-radius: 10px;
    margin-bottom: 40px;
}

.author{
  min-width : 400px;
}
#errorMessage {
    padding-top : 15px;
    color: red;
    margin-right: 20px;
}
button{
  background-color: #f4511e;
  border: none;
  color: white;
  text-align: center;
  font-size: 16px;
  opacity: 0.7;
  transition: 0.3s;
  border-radius: 20px;
  margin:10px;
  height: 50px;
  width: 200px;
}

button:hover {
    opacity: 1;
}
a{
    text-decoration: none;
    color: blueviolet;
    font-size: 17px;
    font-weight: bolder;
}
input {
    height: 40px;
    border: 2px solid blueviolet;
    border-radius: 10px;
    background-color: rgb(233, 233, 249);
    text-align: center;
}

.searchItems {
  display: inline-flexbox;
  align-items: right;
  margin-right: 20px;
  float: right;
  min-width: 700px;
}

#name {
    color : blueviolet;
    font-size: 18px;
    font-weight: bolder;
    margin-left: 40px;
    margin-right: 40px;
}



@media only screen and (max-width: 700px) {
    * {
        width: 100%;
        margin: 0px;
        padding: 0px;
    }

    .menu {
      display: block;
    }

    .searchItems {
      display: block;
      width: 70%;
    }

    .searchItems {
      align-items: right;
      margin-right: 20px;
      float: left;
      min-width: 200px;
}
    
}

</style>