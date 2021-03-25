<template>
  <div>
    Filter Todos:
    <select @change="filterTodos($event)">
      <option value="10">10 </option>
      <option value="30">30 </option>
      <option value="50">50 </option>
      <option value="70">70 </option>
      <option value="90">90 </option>
      <option value="200">200 </option>
    </select>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "FilterTodos",
  methods: mapActions(["filterTodos"]),
};
</script>

<style>
select {
  margin-top: 20px;
  padding: 6px;
  border: #41b883;
}
</style>
