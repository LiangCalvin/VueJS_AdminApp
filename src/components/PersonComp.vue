<template>
  <CardComp>
    <template v-slot:card-header>
      <h1>{{ name }}</h1>
    </template>
    <template v-slot:card-content>
      <transition name="fade">
        <div v-show="isVisibleContent">
          <p>Gender: {{ gender }} Language: {{ lang.join(", ") }}</p>
          <p>Salary: {{ salary }} Position: {{ department }}</p>
        </div>
      </transition>
      
      <button @click="toggleContentVisibility">{{ isVisibleContent ? "Hide Details" : "Show Details" }}</button>&nbsp;
      <button @click="deleteEmployee()">Delete</button>

    </template>
  </CardComp>
</template>

<script>
import CardComp from "./CardComp.vue";
export default {
  name: "PersonComp",
  components: {
    CardComp,
  },
  data() {
    return {
      isVisibleContent: false, // Initialize visibility of additional content
    };
  },
  props: {
    id: {
      type: Number,
    },
    name: {
      type: String,
      required: true,
    },
    salary: {
      type: Number,
      required: true,
      default: 150000,
    },
    department: {
      type: String,
      required: true,
    },
    gender: {
      type: String,
    },
    lang: {
      type: Array,
    },
  },
  methods: {
    toggleContentVisibility() {
      this.isVisibleContent = !this.isVisibleContent;
    },
    deleteEmployee(){
      this.$emit("del",this.id);
    }
  },
};
</script>

<style scoped>
h1 {
  color: rgb(8, 7, 7);
}
li {
  margin: 1rem 0;
  font-size: 1.25rem;
  font-weight: bold;
  background: rgba(24, 212, 96, 0.765);
  padding: 0.5rem;
  color: black;
  border-radius: 25px;
}
button {
  font: inherit;
  cursor: pointer;
  border: 1px solid rgba(1, 1, 1, 0.765);
  background: rgba(176, 214, 191, 0.765);
  color: rgb(14, 12, 12);
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgb(15, 13, 13);
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.5s linear;
}
</style>