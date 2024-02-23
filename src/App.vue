<template>
    <header>
      <h1>System Management</h1>
    </header>
    <FormComp @save="insertEmp"/>
    <section class="emp-content" v-if="employees.length>0">
      <h2>Employee Details</h2>
    <ListData :employees="employees" @delete="deleteEmp" />
    </section>
</template>

<script>
import FormComp from './components/FormComp.vue';
import ListData from "./components/ListData.vue";
import { v4 as uuidv4 } from 'uuid'; // Import the uuid library
export default {
  name: "App",
  components: {
    ListData,
    FormComp
  },
  data(){
    return{
      employees:[],
    }
  },
  methods:{
    insertEmp(data){
      const id = uuidv4();
      const newEmp = { id, ...data };
      this.employees.push(newEmp);
    },
    deleteEmp(id){
      this.employees = this.employees.filter(emp => emp.id !== id);
    }
  },
};
</script>

<style scope>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
header{
  box-shadow: 0.2px 8px rgb(3, 3, 4);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: rgba(24, 212, 96, 0.765);
  color: rgb(5, 4, 4);
  text-align: center;
}
.emp-content {
  box-shadow: 0.2px 8px rgb(156, 163, 196);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: rgb(241, 247, 248);
  color: rgba(31, 45, 36, 0.765);
  text-align: center;
}
.emp-content h2{
  font-size: 2rem;
  border-bottom: 4px solid rgba(31, 45, 36, 0.765);
  color: rgb(4, 3, 4);
  margin: 0 0 1rem 0;
}
</style>