<template>
  <div class="list">
    <transition-group name="list" tag="ul">
      <li v-for="list in orderedJobs" :key="list.id" class="item">
        <h2>
          Type of Job : <span class="call">{{ list.title }}</span>
        </h2>
        <h3>
          Full name : <span class="name">{{ list.name }}</span>
        </h3>

        <h3 class="salary">Monthly Salary: {{ list.salary }} $</h3>
        <p>
          <span>Description : </span>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Aperiam amet
          enim nesciunt neque aliquam reiciendis tempora vitae vero animi
        </p>
      </li>
    </transition-group>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, computed } from "vue";
import List from "@/types/listType";
import Button from "@/types/buttonType";

export default defineComponent({
  props: {
    data: {
      type: Array as PropType<List[]>,
      required: true,
    },
    order: {
      type: String as PropType<Button>,
      required: true,
    },
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.data].sort((a: List, b: List) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return { orderedJobs };
  },
});
</script>

<style scoped>
.list {
  margin-block-start: 5rem;
}
ul {
  padding: 0;
  margin: 0;
  list-style: none;
}

.item {
  background: #fff;
  width: 80%;
  max-width: 1000px;
  padding: 1rem;
  border-radius: 6px;
  margin-block: 1rem;
  margin-inline: auto;
}

h3 {
  margin: 0.5rem;
}

.call {
  color: #ffb156;
}
.salary {
  color: #00ffa2;
}
.name {
  font-family: HyliaSerif;
  letter-spacing: 1px;
  background: #fdfd;
  padding-inline: 1rem;
  border-radius: 6px 0 6px;
}
.list-move {
  transition: all 1s cubic-bezier(0.86, 0, 0.07, 1);
}
</style>
