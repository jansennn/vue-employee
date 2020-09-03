<template>
    <div id="data">
    <sorted-table :values="values">
      <thead>
        <tr>
          <th scope="col" style="text-align: left; width: 10rem;">
            <sort-link name="id">ID</sort-link>
          </th>
          <th scope="col" style="text-align: left; width: 10rem;">
            <sort-link name="name">Name</sort-link>
          </th>
          <th scope="col" style="text-align: left; width: 10rem;">
            <sort-link name="age">Age</sort-link>
          </th>
        </tr>
      </thead>
      <template #body="sort1">
        <tbody>
          <tr v-for="value in sort1.values" :key="value.id">
            <td>{{ value.id }}</td>
            <td>{{ value.name }}</td>
            <td>{{ value.age }}</td>
          </tr>
        </tbody>
      </template>
    </sorted-table>
  </div>
</template>

<script>
import SortedTablePlugin from "vue-sorted-table";
import Vue from 'vue'; 

Vue.use(SortedTablePlugin);
export default {
  name: "App",
  data: function() {
    return {
      values: [
        { name: "Marthin Tampubolon", id: 2, age: 22 },
        { name: "Barack Obama", id: 1, age: 42 },
        { name: "Plugin Foo Bar", id: 3, age: 79 },
        { name: "Andreas Tampubolon", id: 4, age: 20 },
        { name: "nesty", id: 5, age: 18 },
        { name: "Lebron James", id: 6, age: 30 },
        { name: "Leonel Messi", id: 7, age: 30 },
        { name: "Hahah", id: 8, age: 30 },
        { name: "James Rodriguez", id: 9, age: 30 },
        { name: "Siapa ya", id: 10, age: 30 }
      ]
    };
  }
};
</script>