<template>
    <div id="dropdown-div">
        <label for="users">Select Users:</label>
        <br />
        <select v-model="selected">
            <option value disabled>Please Select a User</option>
            <option v-bind:value="user.name" v-for="user in users" :key="user.id"
                >{{ user.name }} | ID: {{ user.id }}</option
            >
        </select>
        <p>Current user selected: {{ selected }}</p>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'CynDropdown',
    data() {
        return {
            users: null,
            selected: 'None',
            defaultSelected: 'Please select a user'
        };
    },
    created() {
        axios
            .get('https://jsonplaceholder.typicode.com/users')
            .then(res => {
                this.users = res.data;
            })
            .catch(err => {
                this.users = 'An error has occured: ' + err;
            });
    }
};
</script>

<style scoped></style>
