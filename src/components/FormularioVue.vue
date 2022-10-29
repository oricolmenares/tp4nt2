<template>
  <div>
    <form @submit.prevent="submitForm">
      <span>Full Name</span><br>
      <input 
        v-model="name"
        type="text"
        placeholder="Enter your name" 
        minlength="3"
      /><br>
      <span>Email</span><br>
      <input 
        v-model="email"
        type="email"
        placeholder="Enter your email" 
      /><br>
      <span>Edad</span><br>
      <input 
        type="number" 
        v-model="edad" 
        :min=16
        :max=110 
      /><br>
      <input 
        class="submit" 
        type="submit" 
        value="Submit"
      >
    </form>
    <table v-if="formSubmitted">
      <tr>
        <th>Nombre</th>
        <th>Email</th>
        <th>Edad</th>
      </tr>
      <tr>
        <th> {{ name }} </th>
        <th> {{ email }} </th>
        <th> {{ edad }} </th>
      </tr>
    </table>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: "",
        email: "",
        edad: "",
        formSubmitted: false
      };
    },
    methods: {
      submitForm: function () {
        this.formSubmitted = true
      }
    },
  };
</script>
<style>
  form {
    padding: 10px;
    border: 2px solid black;
    border-radius: 5px;
  }

  input {
    padding: 4px 8px;
    margin: 4px;
  }

  span {
    font-size: 18px;
    margin: 4px;
    font-weight: 500;
  }

  .submit {
    font-size: 15px;
    color: #fff;
    background: #222;
    padding: 6px 12px;
    border: none;
    margin-top: 8px;
    cursor: pointer;
    border-radius: 5px;
  }

</style>
