<template>
<div>
    <Header />
    <div class="wrapper container mx-auto">
        <h2 class="text-center text-4xl mt-12">Hi {{name}} ! Welcome to our website.</h2>
    </div>
    <table class="table-auto w-3/4 mx-auto border p-4 rounded my-4">
        <thead class="bg-gray-600 py-2 text-2xl text-white">
            <tr>
                <td class="px-2 py-1">ID</td>
                <td class="px-2 py-1">Name</td>
                <td class="px-2 py-1">Address</td>
                <td class="px-2 py-1">Contact</td>
                <td class="px-2 py-1">Actions</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in restuarants" :key="item.id" class="border-b hover:bg-gray-200 transition-all">
                <td class="border-x px-2 py-1">{{item.id}}</td>
                <td class="border-x px-2 py-1">{{ item.name }}</td>
                <td class="border-x px-2 py-1">{{ item.address }}</td>
                <td class="border-x px-2 py-1">{{ item.contact }}</td>
                <td class="border-x px-2 py-1 flex gap-4 items-center justify-center">
                    <router-link :to="'/update-restuarant/'+item.id">
                        <img src="../assets/edit.png" alt="">
                    </router-link>
                    <router-link :to="'/delete-restuarant/'+item.id">
                        <img src="../assets/delete.png" alt="">
                    </router-link>
                </td>
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
    data() {
        return {
            name: '',
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

        this.restuarants = result.data
    }
}
</script>

<style>

</style>
