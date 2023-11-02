<template>
    <!-- <div class="user-profile">
      <h1>User Profile</h1>
      <div class="profile-form">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="name" @input="updateUserProfile" />
  
        <label for="age">Age:</label>
        <input type="number" id="age" v-model.number="age" @input="updateUserProfile" />
  
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" @input="updateUserProfile" />
      </div>
      <div class="user-data">
        <h2>Your Profile</h2>
        <p><strong>Name:</strong> {{ name }}</p>
        <p><strong>Age:</strong> {{ age }}</p>
        <p><strong>Email:</strong> {{ email }}</p>
      </div>
    </div> -->



    <div class="container">
  <h2>User Form</h2>
  <form>
    <div class="form-group">
      <label for="name">Name:</label>
      <input type="text" class="form-control" id="name" v-model="name" @input="updateUserProfile" placeholder="Enter Name">
    </div>
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" class="form-control" id="email" v-model="email" @input="updateUserProfile" placeholder="Enter email">
    </div>
    <div class="form-group">
      <label for="name">Age:</label>
      <input type="text" class="form-control" id="name" v-model.number="age" @input="updateUserProfile" placeholder="Enter Age">
    </div>

    <!-- <button type="submit" class="btn btn-default">Submit</button> -->
  </form>


</div>

<div class="user-data">
        <h2>Your Profile</h2>
        <p><strong>Name:</strong> {{ name }}</p>
        <p><strong>Age:</strong> {{ age }}</p>
        <p><strong>Email:</strong> {{ email }}</p>
      </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        age: '',
        email: ''
      };
    },
    created() {
      this.fetchUserProfileData();
    },
    mounted() {
      // Perform additional setup or interact with the DOM here
    },
    methods: {
      fetchUserProfileData() {
        // Simulate fetching user data from an API
        setTimeout(() => {
          this.name = 'Junaid Khan';
          this.age = 20;
          this.email = 'mjuanidkhan94@gmail.com';
        }, 1000); // Simulating an API call with a delay
      }
    }
  };
  </script>
  
  <style scoped>
  .user-profile {
    font-family: Arial, sans-serif;
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
  }
  
  .profile-form label {
    font-weight: bold;
  }
  
  .profile-form input {
    width: 100%;
    padding: 5px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 3px;
  }
  
  .user-data {
    margin-top: 20px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    background-color: #fff;
  }

  .form-control{
    font-size: 30px;
    height: 65px !important;
  }
  </style>