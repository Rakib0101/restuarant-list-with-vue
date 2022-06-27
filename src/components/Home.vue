<template>
<div>
    <Header />
    <div class="wrapper container mx-auto">
        <h2 class="text-center text-4xl mt-12">Hi {{name}} ! Welcome to our website.</h2>
    </div>
    <table class="table-auto w-1/2 mx-auto border p-4 rounded my-4">
        <thead  class="bg-gray-600 py-2 text-2xl text-white">
            <tr>
                <td>ID</td>
                <td>Name</td>
                <td>Address</td>
                <td>Contact</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in restuarants" :key="item.id" class="border-b hover:bg-gray-200 transition-all">
                <td>{{item.id}}</td>
                <td>{{ item.name }}</td>
                <td>{{ item.address }}</td>
                <td>{{ item.contact }}</td>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
import axios from "axios";
import Header from './Header.vue'
export default {
    name: "Home",
    components: {
        Header
    },
    data(){
        return{
            name:'',
            restuarants: []
        }
    },
    async mounted() {
        let user = localStorage.getItem('user-info');
        this.name = JSON.parse(user).name
        if (!user) {
            this.$router.push({
                name: 'SignUp'
            })
        }
        let result = await axios.get("http://localhost:3000/restuarants")
        
        this.restuarants= result.data
    }
}
</script>

<style>

</style>
