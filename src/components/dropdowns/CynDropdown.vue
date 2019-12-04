<template>
  <div id="dropdown-div">
    <label for="users">Select an Item:</label>
    <br />
    <select v-model="selectedItem">
      <option value disabled>Please Select an item</option>
      <option
        v-for="item in items"
        :value="item.name"
        :key="item.id"
        v-on:click="selectedItem = item">
        {{ item.name }} | ID: {{ item.id }}</option>
    </select>
    <p>Current user selected: {{ selectedItem }}</p>
  </div>
</template>

<script>
export default {
  name: "CynDropdown",
  props: {
    items: Array
  },
  data() {
    return {
      selectedItem: "None"
    };
  }
};
</script>

<style scoped>
</style>
