<template>
    <div class="names" ref="usernames">
        <h3 v-for="user in users" :key="user[`id`]">{{ user[`email`] }}</h3>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        mounted () {
            axios.request({
                url: `https://reqres.in/api/users`
            }).then((response) => {
                   this.users = response[`data`][`data`];
                
            }).catch((error) => {
                alert(`please, refresh the page`);
                console.log(error);
            });
        },

        data() {
            return {
                users: []
            }
        },
    }
</script>

<style scoped>
.names {
    display: grid;
    grid-auto-flow: column;
}
</style>