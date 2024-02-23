<template>
  <div>
    <ul>
        <PersonComp 
            v-for="(item,index) in employees"
            :key = "index"
            :id = "item.id"
            :name = "item.name"
            :salary = "item.salary"
            :gender = "item.gender"
            :lang = "item.lang"
            :department = "item.department"
            :isVisible = "item.isVisible"
            @del = "removeEmp"
        />
    </ul>
    
  </div>
</template>

<script>
import PersonComp from './PersonComp.vue'
export default {
  name: "ListData",
  props:[
    "employees"
  ],
  components:{
    PersonComp
  },
  methods:{
    removeEmp(id){
      this.$emit("delete", id);
    }
  },
};
</script>

<style scoped>
ul {
    list-style: none;
    margin: 1rem 0;
    padding: 0;
}

</style>