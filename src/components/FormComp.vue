<template>
  <form @submit.prevent="submitForm">
    {{ mess }}
    <div class="form-control">
      <label for="emp-name">Name</label>
      <input type="text" v-model.trim="employee.name" />
    </div>
    <div class="form-control">
      <label for="emp-salary">Salary</label>
      <input type="number" v-model.trim="employee.salary" />
    </div>
    <div class="form-control">
      <label for="department">Position</label>
      <select v-model="employee.department" id="">
        <option value="Marketing">Marketing</option>
        <option value="Accountant">Accountant</option>
        <option value="Programmer">Programmer</option>
      </select>
    </div>
    <div class="form-control">
      <h2>Gender</h2>
      <div>
        <input type="radio" value="Male" v-model="employee.gender">
        <label for="gender-name">Male</label>
      </div>
      <div>
        <input type="radio" value="Female" v-model="employee.gender">
        <label for="gender-name">Female</label>
      </div>
      <div>
        <input type="radio" value="Others" v-model="employee.gender">
        <label for="gender-name">Other</label>
      </div>
    </div>
    <div class="form-control">
      <h2>Language</h2>
      <div>
        <input type="checkbox" value="English" v-model="employee.lang">
        <label for="lang">English</label>
      </div>
      <div>
        <input type="checkbox" value="Russian" v-model="employee.lang">
        <label for="lang">Russian</label>
      </div>
        <div>
        <input type="checkbox" value="Chinese" v-model="employee.lang">
        <label for="lang">Chinese</label>
      </div>
    </div>
    <div>
      <button>Add</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "FormComp",
  data() {
    return {
      employee: {
        name: "",
        salary: 0,
        department: "",
        gender: "",
        lang:[],
      },
      mess: "Add New Employee",
    };
  },
  methods:{
    submitForm(){
      const newEmp = {
        name: this.employee.name,
        salary: this.employee.salary,
        department: this.employee.department,
        lang: this.employee.lang,
        gender: this.employee.gender
      }
      this.$emit("save",newEmp);
      this.resetForm();
    },
    resetForm(){
      this.employee.name = "";
      this.employee.salary = 0;
      this.employee.department = "";
      this.employee.gender = "";
      this.employee.lang = [];
    }
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.25);
  padding: 2rem;
  background: white;
}
.form-control {
  margin: 0.5rem 0;
}
label {
  font-weight: bold;
}
input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}
button {
  font: inherit;
  background: purple;
  color: white;
  cursor: pointer;
  padding: 0.25rem 1.5rem;
  border-radius: 15px;
}
input[type="radio"], input[type="checkbox"] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}
input[type="radio"]+label,input[type="checkbox"]+label{
  font-weight: normal;
}
h2{
  font-size: 1rem;
  margin: 0.5rem 0;
}
</style>