<!-- ParentComponent.vue -->
<template>
  <div>
   
      <md-card v-for="item in items"
    :key="item.id" :item="item">
       

        <md-card-area>
          <md-card-header>
            <md-card-media>
              <img src=#>

        </md-card-media>
            <span class="md-title">{{item.eve}}</span>
           
           
           
          </md-card-header>
           <md-card-content>
            <p>VENUE:{{item.venue}}</p>
          <p> DATE:{{item.DT}}</p>
          <p> Ph no:{{item.contact}}</p>
        </md-card-content>

        </md-card-area>
   
    </md-card>
  </div>
</template>
<style>
  .md-card {
    width: 320px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
  }
</style>

<script>


export default {
  components: {
   
  },
  data() {
    return {
      items: [] // Data fetched from the API will be stored here
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('http://127.0.0.1:8000/api/Event/');
        const data = await response.json();
        this.items = data; // Assuming API returns an array of items
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }
  }
};
</script>