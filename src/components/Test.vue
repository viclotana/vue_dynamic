<template>
  <div id="visa">
    <h1>Vue Visa Application</h1>
    <form>
      <label for="first name">First Name:</label>
      <input type="text" required>
      <br>
      <label for="last name">Last Name:</label>
      <input type="text" required>
      <br>
      <label for="country">Nationality:</label>
      <input type="text"  required>
      <br>
      <label for="passport number">Passport Number:</label>
      <input type="text"  required>
  
      <label for="duration">Duration of stay:</label>
      <input type="text"  required>
     <br><br>
      <button @click="addVisa">Add another previous visa</button>
      <br>
      <div class="previous"
      v-for="(applicant, counter) in applicants"
      v-bind:key="counter">
        <span @click="deleteVisa(counter)">x</span>
        <label for="duration">{{counter+1}}. Previous Visa:</label>
        <input type="text" v-model.lazy="applicant.previous" required>
        <label for="duration">Year of expiration:</label>
        <input type="text" v-model.lazy="applicant.expiration" required> 
      </div>
    </form>

  </div>
</template>

<script>
export default {
  name: 'Test',
  props: {
    msg: String
  },
  data(){
    return {
       applicants:[
       {
      previous: '',
      expiration:''
       }
     ]
    }
  },
  methods : {
    addVisa(){
      this.applicants.push({
        previous:'',
        expiration: ''
      })
    },
    deleteVisa(counter){
      this.applicants.splice(counter,1);

    }
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#visa {
  margin: 20px auto;
  max-width: 700px;
}
label{
  display: block;
  margin: 20px 0 10px;
}
input {
  font-size: 30px;
  border: 1px double rgb(102, 97, 96) ;
  border-radius: 4px;
}
button {
  font-size: 16px;
 background: rgb(64, 179, 140);
  padding: 0.4rem 1.3rem;
  text-align: center;
  border: none;
  cursor: pointer;
  border-radius: 4px;
 margin: 10px;
}
span{
  width: 30px;
  float: right;
  cursor: pointer;
}
span:hover{
  color: brown;
}
.previous{
  border: 1.5px solid;
  padding:5px;
  margin-bottom: 10px;
}
</style>
