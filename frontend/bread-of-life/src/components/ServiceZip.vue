<template>
    <div class="row">
    <!--Table to display client service by zipcode-->
        <div class="col-md-12">
            <table class="table table-striped">
                <thead class="thead-dark">
                    <tr>
                        <th>Event Type</th>
                        <th>First Name</th>
                        <th>Last Name</th>
                        <th>City</th>
                        <th>State</th>
                        <th>Phone</th>
                        <th>Count</th>
                    </tr>
                </thead>
                <tbody>
                <!--Passing the customer servicebyzipcode with the matching phone number , and how time customer attend the event -->
                    <tr v-for="servicebyzip in Zip" :key="servicebyzip.phoneNumber">
                        <td>{{ servicebyzip.eventType }}</td>
                        <td>{{ servicebyzip.firstName }}</td>
                        <td>{{ servicebyzip.lastName }}</td>
                        <td>{{ servicebyzip.city }}</td>
                        <td>{{ servicebyzip.state }}</td>
                        <td>{{ servicebyzip.phoneNumber }}</td>
                        <td>{{ servicebyzip.COUNT }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
// use axios to send http request and return the customer attend by zipcode
    import axios from "axios";
    export default {
        data() {
            return {
                Zip: []
            }
        },
        // this is using created hook 
        created() {
            let apiURL = 'http://localhost:3000/viewbyzip';
            axios.get(apiURL).then(res => {
                this.Zip = res.data;
            }).catch(error => {
                console.log(error)
            });
        }
    }
</script>



<style>
    .btn-success {
        margin-right: 10px;
    }
</style>
