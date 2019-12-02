<template>
  <div id="dropdown-div">
    <label for="users">Select an Item:</label>
    <br />
    <select @change="onChange($event)">
      <option value disabled selected>Please Select an item</option>
      <option
        v-for="item in items"
        :value="item.name"
        :key="item.id"
      >{{ item.name }} | ID: {{ item.id }}</option>
    </select>
    <p>Current user selected: {{ selectedItem }}</p>
  </div>
</template>

<script>
export default {
  name: "CynDropdown",
  props: {
    items: Array,
    selectedItem: String
  },
  methods: {
    onChange(event) {
      console.log(event.target.value);
      this.selectedItem = event.target.value;
    }
  }
};
</script>

<style scoped>
</style>
