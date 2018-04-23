<template>
  <div class="test">
    <h1>{{title}}</h1>
    <hr />
    <h3 v-if="user.firstName">Welcome, {{user.firstName}}!</h3>
    <h3 v-else>Welcome!</h3>
    <label>First Name: </label><input type="text" v-model="user.firstName">
    <br />
    <label>Last Name: </label><input type="text" v-model="user.lastName">
    <br />
    <label>Phone Number: </label><input type="text" v-model="user.phoneNumber">
    <br />
    <label>Street Address: </label><input type="text" v-model="user.streetAddress">
    <br />
    <label>Apartment: </label><input type="text" v-model="user.apartment">
    <br />
    <label>City: </label><input type="text" v-model="user.city">
    <br />
    <label>State: </label><input type="text" v-model="user.state">
    <br />
    <label>ZIP Code: </label><input type="text" v-model="user.zip">
    <br />
    <h3>Please list your collegiate experience(s)</h3>
    <ul class="plain">
      <li v-for="(college, input) in colleges">
        <label>College: </label><input type="text" v-model="college.collegeName">
        <br />
        <label>Major: </label><input type="text" v-model="college.collegeMajor">
        <br />
        <label>Degree Type (e.g., B.A.): </label><input type="text" v-model="college.collegeDegreeType">
        <br />
        <label>GPA: </label><input type="text" v-model="college.collegeGPA">
        <br />
        <label>Year Graduated (YYYY): </label><input type="text" v-model="college.collegeYear">
        <br />
      </li>
    </ul>
    <button @click="addNewCollege">Add new college</button>

    <h3>Please list your previous <u>full-time</u> work experience, starting with the most recent</h3>
    <ul class="plain" v-for="(company, input) in companies">
      <li>
        <label>Company Name: </label><input type="text" v-model="company.companyName">
        <br />
        <label>Position Title: </label><input type="text" v-model="company.companyPosition">
        <br />
        <label>Start Date: </label><input type="text" v-model="company.companyStart">
        <br />
        <label>End Date: </label><input type="text" v-model="company.companyEnd">
        <br />
        <label>Position Responsibilities: </label><br /><textarea rows="5" style="width:500px;" v-model="company.companyResp" placeholder="Enter position responsibilites.  Press 'Return' to start a new line."></textarea>
      </li>
    </ul>
    <button @click="addNewCompany">Add new job</button>

    <hr />
    <div class="plain">
      <p><b>{{fullName}}</b></p>
      <p >{{phoneNumber}}<br /> {{streetAddress}} <br /><span v-if="apartment">Apartment {{apartment}}<br /></span> {{address}}</p>
    </div>
    <h3 class="left">Education</h3>
    <ul class="plain" v-for="(college, input) in colleges">
      <li v-if="college.collegeDegreeType"><b>{{college.collegeName}} GPA: {{college.collegeGPA}}</b></li>
      <li v-if="college.collegeMajor">{{college.collegeDegreeType}}, {{college.collegeMajor}} - {{college.collegeYear}}</li>
    </ul>
    <h3 class="left">Work Experience</h3>
    <ul class="plain" v-for="(company, input) in companies">
      <li><b>{{company.companyName}} - {{company.companyStart}} - {{company.companyEnd}}</b></li>
      <li><i>{{company.companyPosition}}</i></li>
      <li style="white-space: pre-line">{{company.companyResp}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'test',
  props: {},
  data() {
    return {
      title: 'Vue.JS Resume Builder',
      colleges: [],
      companies: [],
      user: {
        firstName: 'Alex',
        lastName: 'Middleton',
        phoneNumber: '843-696-4677',
        streetAddress: '130 River Landing Drive',
        apartment: '3206',
        city: 'Charleston',
        state: 'SC',
        zip: '29492'
      }
    }
  },
  methods: {
    greet: function(greeting) {
      alert(greeting)
    },
    addNewCollege() {
      this.colleges.push({
        collegeName: '',
        collegeMajor: '',
        collegeDegreeType: '',
        collegeGPA: '',
        collegeYear: ''
      })
    },
    addNewCompany() {
      this.companies.push({
        companyName: '',
        companyPosition: '',
        companyStart: '',
        companyEnd: '',
        companyResp: ''
      })
    }
  },
  computed: {
    fullName: function() {
      return `${this.user.firstName} ${this.user.lastName}`
    },
    phoneNumber: function() {
      return `${this.user.phoneNumber}`
    },
    streetAddress: function() {
      return `${this.user.streetAddress}`
    },
    apartment: function() {
      return `${this.user.apartment}`
    },
    address: function() {
      return `${this.user.city}, ${this.user.state} ${this.user.zip}`
    }
  }
}
</script>

<style scoped>
.plain {
  list-style-type: none;
  padding: 0;
},
.left {
  text-align: left;
  margin-top: 0px;
}
</style>
