<template>
  <div>
    <CynDropdown :items="items" :selected="selected" />
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
      selected: "None"
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
