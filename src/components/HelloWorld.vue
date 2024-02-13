<script setup>
  import { ref } from 'vue';
  import jsonData from '../../db.json'; // Import the JSON file

  // Define your reactive data for lot number and lot data
  const lotNumber = ref('');
  const lotData = ref(null);

  // Define your method for handling form submission and data retrieval
  const handleSubmit = () => {
    console.log(lotNumber.value);
    // Find the lot data in the database
    const foundLot = jsonData.find(item => item.lotNumber === lotNumber.value);

    // If lot data found, assign it to lotData, else set it to null
    lotData.value = foundLot ? foundLot : null;
    console.log(lotData.value);
  };
</script>

<!-- Export reactive data and method -->
<!-- <script>
  export { lotNumber, lotData, handleSubmit };
</script> -->






<template>
  <!-- Your template code goes here -->
  <h1>Farm to Fork Tracker</h1>

  <div id="app">
    <form @submit.prevent="handleSubmit">
      <label class="form-title" for="lotNumber">Enter Lot Number: </label>
      <input class="form-box" type="text" id="lotNumber" name="lotNumber" v-model="lotNumber"><br><br>
      <input class ="form-button" type="submit" value="Submit">
    </form>
    <br>
    <hr>
    <div v-if="lotData">
      
      <h2 class="farm-title">{{ lotData.farm }}</h2>

      <br>

      <div class="farm-info">
        <p class="about-farm">{{ lotData.aboutFarm }}</p>
        <img class ="farm-photo" :src="lotData.photo" alt="Farm Image" width="300" height="200">
      </div>
      
      <br>
      <br>

      <div class="more-farm">
        <h3>Our Growing Process for Lot {{ lotData.lotNumber }}:</h3>
        <p class="about-farm">{{ lotData.growingProcess }}</p>
        <br>
        <h3>Product: {{ lotData.product }}</h3>
        <h3>Harvest Location: {{ lotData.location }}</h3>
        <h3>Harvest Date: {{ lotData.datePicked }}</h3>
        <h3>Date Shipped: {{ lotData.dateShipped }}</h3>
        <h3>Date Received: {{ lotData.dateReceived }}</h3>

      </div>

    </div>
  </div>
</template>

<style scoped>
h1 {
  font-family: 'Futura';
  font-weight: bold;
  font-size: 4em;
}
.form-title {
  font-family: 'Futura';
  font-weight: bold;
  font-size: 2em;
}
.form-box {
  font-family: 'Futura';
  font-size: 1.5em;
  border-radius: 10px;
  padding: 0.5em;
}
.form-button {
  font-family: 'Futura';
  font-size: 1.5em;
  border-radius: 10px;
  padding: 0.5em;
  background-color: #cbb38b;
  color: white;
  border: none;
}
.form-button:hover {
  background-color: #a88e6f;
  color: black;
  cursor: pointer;
}
.farm-title {
  font-family: 'Futura';
  font-weight: bold;
  font-size: 3em;
}
.farm-info {
  display: flex;
}
.farm-photo {
  margin-left: 2em;
  margin-right: 5em;
  border-radius: 10px;
  width: 40%;
  height: 40%;
}
.about-farm {
  margin-right: 2em;
  margin-left: 5em;
  font-weight: italic;
  font-family: 'Futura';
  font-size: 1.5em;
}

h3 {
  font-family: 'Futura';
  font-weight: bold;
  font-size: 2em;
}
</style>
