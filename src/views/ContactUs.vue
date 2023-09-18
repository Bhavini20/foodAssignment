<template>
  <div class="contact-container">
    <h2 class="contact-heading">Contact Us</h2>
    <div class="form-container">
      <form @submit.prevent="submitForm" class="contact-form">
        <div class="form-group">
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="formData.name" required>
        </div>
        <div class="form-group">
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="formData.email" required>
        </div>
        <div class="form-group">
          <label for="message">Message:</label>
          <textarea id="message" v-model="formData.message" required></textarea>
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>
    <div style="padding-top: 2rem;" class="contact-heading">OUR LOCATION</div>
    <div id="map" class="google-map"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
        email: '',
        message: ''
      }
    };
  },
  mounted() {
    this.initMap();
  },
  methods: {
    submitForm() {
      console.log('Form submitted with data:', this.formData);

      this.formData.name = '';
      this.formData.email = '';
      this.formData.message = '';
    },
    initMap() {
      // Coordinates for Khajaguda, Hyderabad
      const khajagudaLocation = { lat: 17.4105, lng: 78.3917 };

      // Create a map centered at the specified location
      this.map = new google.maps.Map(document.getElementById('map'), {
        center: khajagudaLocation,
        zoom: 15, // Adjust the zoom level as needed
      });

      // Create a marker for the office location
      const marker = new google.maps.Marker({
        position: khajagudaLocation,
        map: this.map,
        title: 'Our Office Location',
      });
    },
  }
};
</script>

<style scoped>
.contact-container {
  display: flex;
  flex-direction: column;
  padding-top: 2rem;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #f0f0f0; /* Set your desired background color */
}

.contact-heading {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333; /* Set your desired text color */
}

.form-container {
  width: 50%;
  background-color: #fff; /* Set your desired form background color */
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
}

.contact-form {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 20px;
}

label {
  font-weight: bold;
}

input[type="text"],
input[type="email"],
textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  background-color: #007BFF;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.google-map {
  width: 70%;
  height: 300px; /* Adjust the height as needed */
  margin-top: 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
