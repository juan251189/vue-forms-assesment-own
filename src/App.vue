<template>
<div class="container">
  <form v-if="!submitted">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <!-- Exercise 1 -->
        <!-- Create a Signup Form where you retrieve the following Information -->
        <!-- Full Name (First Name + Last Name) -->
        <!-- Mail -->
        <!-- Password -->
        <!-- Store Data? Yes/No -->



        <div class="form-group">
          <label for="exampleInputName2">Name</label>
          <input type="text" id="name" class="form-control"  v-model="userDetails.name">
        </div>
        <div class="form-group">
          <label for="lastname">Last Name</label>
          <input id="lastname " type="text" class="form-control"  v-model="userDetails.lastName">
        </div>



        <div class="form-group">
          <label for="mail">Mail</label>
          <input type="mail" id="mail" class="form-control" v-model="userDetails.mail">
        </div>

        <div class="form-group">
          <label for="password">Password</label>
          <input type="password" class="form-control" v-model="userDetails.password">
        </div>



        <hr>
        Store Data?
        <div id="storeon" @click="storeData=true" :class="{active:storeData}">
          Yes
        </div>
        <div id="storeoff" @click="storeData=false" :class="{active:!storeData}">
          No
        </div>
        <br>
        <button class="btn btn-primary" @click="submitForm">Submit</button>

        <!-- Exercise 2 -->
        <!-- DONE  Only display the Form if it has NOT been submitted -->
        <!--  DONE Display the Data Summary ONCE the Form HAS been submitted -->

        <!-- Exercise 3 -->
        <!-- Edit the Example from above and create a custom "Full Name" Control -->
        <!-- which still holds the First Name and Last Name Input Field -->
      </div>
    </div>
  </form>
  <hr>
  <div class="row" v-if="submitted">
    <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
      <div class="panel panel-default">
        <div class="panel-heading">
          <h4>Your Data</h4>
        </div>
        <div class="panel-body">
          <p style="white-sapce:pre">Full Name:{{userDetails.fullName}} </p>
          <p>Mail: {{userDetails.mail}}</p>
          <p>Password: {{userDetails.password}}</p>
          <p>Store in Database?:{{storeData}} </p>
        </div>
      </div>
    </div>
  </div>
  <div class="col-12 alert alert-success" v-if="submitted">
    Form sent successfully
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      userDetails: {
        name: '',
        lastName: '',
        fullName: '',
        mail: '',
        password: ''
      },
      storeData: false,
      submitted: false
    }
  },
  methods: {
    submitForm() {
      this.fullName();
      this.submitted = true;

    },
    fullName() {
      this.userDetails.fullName = this.userDetails.name+' ' +this.userDetails.lastName;
    }
  }
}
</script>

<style>
#storeon,
#storeoff {
  width: 40px;
  height: 20px;
  background-color: lightgray;
  padding: 2px;
  display: inline-block;
  margin: 10px -2px;
  box-sizing: content-box;
  cursor: pointer;
  text-align: center;


}

#storeon:hover,
#storeon.active {
  background-color: lightgreen;

}

#storeoff:hover,
#storeoff.active {
  background-color: lightcoral;

}
</style>
