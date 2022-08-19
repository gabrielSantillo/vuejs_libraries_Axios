<template>
    <div class="names">
        <h3 ref="usernames"></h3>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        mounted () {
            axios.request({
                url: `https://reqres.in/api/users`
            }).then((response) => {
                for(let i = 0; i < response[`data`][`data`].length; i++) {
                   this.$refs[`usernames`][`innerHTML`] += response[`data`][`data`][i][`first_name`];
                }
                
            }).catch((error) => {
                alert(`please, refresh the page`);
                console.log(error);
            });
        },
    }
</script>

<style scoped>
.names {
    display: grid;
    grid-auto-flow: column;
}
</style>