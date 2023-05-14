<template>
  <div class="app">
    <header>
      <div class="logo">
        <img src="./assets/heart.svg" alt="site logo" />
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="chnageOrder('title')">Order By Title</button>
        <button @click="chnageOrder('name')">Order By Name</button>
        <button @click="chnageOrder('salary')">Order By Salary</button>
      </div>
    </header>
    <JobList :data="data" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "@/components/JobList.vue";
import List from "@/types/listType";
import Button from "@/types/buttonType";

export default defineComponent({
  components: {
    JobList,
  },
  setup() {
    const data = ref<List[]>([
      { id: 1, name: "Khlaid Abdou", title: "Front End", salary: 7000 },
      { id: 2, name: "Jhon Deo", title: "Dev Ops", salary: 9000 },
      {
        id: 3,
        name: "Ahmed Said",
        title: "WordPress Developer",
        salary: 30000,
      },
      { id: 4, name: "Khalil Elmasry", title: "Web Design", salary: 10000 },
      { id: 5, name: "Fouaad Ali", title: "Web Developer", salary: 6000 },
      { id: 6, name: "Frid abdelkarim", title: "Back End", salary: 8000 },
    ]);

    const order = ref<Button>("name");

    const chnageOrder = (term: Button): void => {
      order.value = term;
    };

    return { data, order, chnageOrder };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header > .logo {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
