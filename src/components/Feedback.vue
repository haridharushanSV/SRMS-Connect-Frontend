<template>
<div :style="{'background-image':'url(https://mcet.in/conference/ICDIIS-20/assets/img/clg.jpg)'}">
    <md-card>
      <md-card-header>
        <div class="md-title">Am I Clean</div>
      </md-card-header>

      <md-card-content>
          
        <md-field>
          <label>Name</label>
          <md-input v-model="name"></md-input>
          </md-field>

          <md-field>
          <label>RollNo.</label>
          <md-input v-model="roll"></md-input>
        </md-field>


        <md-field>
          <label for="movie">Class</label>
          <md-select v-model="cls" name="cls" id="cls">
            <md-option value="UG-1styear">UG-1styear</md-option>
            <md-option value="UG-2ndyear">UG-2ndyear</md-option>
            <md-option value="UG-3rdyear">UG-3rdyear</md-option>
            <md-option value="UG-4thyear">UG-4thyear</md-option>
            <md-option value="PG-1styear">PG-1styear</md-option>
            <md-option value="PG-2ndyear">PG-2ndyear</md-option>
          </md-select>
        </md-field>


      


      <md-field>
          <label for="movie">Place</label>
          <md-select v-model="plc" @input="checkWord" name="plc" id="plc">
            <md-option value="College">College</md-option>
            <md-option value="Hostel">Hostel</md-option>
          </md-select>
      </md-field>


      <md-field v-if="plc === 'College'">
         <md-select v-model="dplc" placeholder="Where in College">
            <md-option value="A-Block">A-Block</md-option>
            <md-option value="B-Block">B-Block</md-option>
            <md-option value="C-Block">C-Block</md-option>
            <md-option value="DiamondJubliee-Block">DiamondJubliee-Block</md-option>  
            <md-option value="Parking">Parking</md-option>
            <md-option value="Ground">Ground</md-option>
          </md-select> 
      </md-field>


      <md-field v-if="plc === 'Hostel'">
          <md-select v-model="dplc" placeholder="Where in Hostel">
            <md-option value="groundfloor">groundfloor</md-option>
            <md-option value="1stFloor">1stFloor</md-option>
            <md-option value="2ndFloor">2ndFloor</md-option>
            <md-option value="3rdFloor">3rdFloor</md-option>  
          </md-select>  
      </md-field>


      <md-field>
        <label>Problem Here</label>
        <md-textarea v-model="prb" value="problem"></md-textarea>
      </md-field>


      <md-field>
       <label>Upload files</label>
       <md-file v-model="img" placeholder="Images if any" />
      </md-field>

      </md-card-content>
    </md-card>
        
  </div>
</template>

<style scoped>
  .md-card {
    width: 500px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
  }
</style>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      postData: {
        name: '',
        roll: '',
        cls:'',
        plc:'',
        dplc:'',
        prb:'',
        img:''

      }
    };
  },
  methods: {
    submitData() {
      axios.post('http://127.0.0.1:8000/api/login/', this.postData)
        .then(response => {
          console.log('Response:', response.data);
          // Do something with the response
        })
        .catch(error => {
          console.error('Error:', error);
          // Handle error
        });
    }
  }
};
</script>