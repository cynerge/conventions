<template>
  <div id="dropdown-div">
    <label for="users">Select Users:</label>
    <br />
    <select v-model="selected">
      <option disabled>Please Select a User</option>
      <option
        :value="items.name"
        v-for="item in items"
        :key="item.id"
      >{{ item.name }} | ID: {{ item.id }}</option>
    </select>
    <p>Current user selected: {{ selected }}</p>
  </div>
</template>

<script>
export default {
  name: "CynDropdown",
  props: {
    items: Array,
    selected: String
  }
};
</script>

<style scoped></style>
