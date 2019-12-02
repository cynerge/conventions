<template>
  <div>
    <CynDropdown :items="items" :selectedItem="selectedItem" />
  </div>
</template>

<script>
import CynDropdown from "../components/dropdowns/CynDropdown";
import axios from "axios";
export default {
  name: "dropdowns",
  components: {
    CynDropdown
  },
  data() {
    return {
      items: [],
      selectedItem: "None"
    };
  },
  mounted() {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then(res => {
        this.items = res.data;
      })
      .catch(err => {
        this.items = "An error has occured: " + err;
      });
  }
};
</script>

<style></style>
