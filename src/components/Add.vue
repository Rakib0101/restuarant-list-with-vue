<template>
<div>
    <Header />
    <div class="wrapper container mx-auto">
        <h2 class="text-3xl font-semibold my-8">Add Restuarant</h2>
        <form action="" class="add-form w-2/3 border-2 border-green-500 rounded shadow-md p-12">
            <label class="block text-left" for="name">Restuarant Name:</label>
            <input class="block border rounded-sm w-full mb-2 p-1" type="text" id="name" placeholder="enter restuarant name" v-model="restuarant.name">
            <label class="block text-left" for="address">Restuarant Address:</label>
            <input class="block border rounded-sm w-full mb-2 p-1" type="text" id="address" placeholder="enter restuarant address" v-model="restuarant.address">
            <label class="block text-left" for="contact">Contact Number:</label>
            <input class="block border rounded-sm w-full mb-2 p-1" type="text" id="contact" placeholder="enter contact number" v-model="restuarant.contact">
            <button type="button" class="border rounded bg-green-500 text-white px-2 py-1" v-on:click="addRestuarant">Add New Restuarant</button>
        </form>
    </div>
</div>
</template>

<script>
import axios from "axios";
import Header from './Header.vue'
export default {
    name: "Add",
    components: {
        Header
    },
    data(){
        return{
            restuarant:{
                name: '',
                address: '',
                contact: '',
            }
        }
    },
    methods:{
        async addRestuarant(){
            let result = await axios.post("http://localhost:3000/restuarants", {
                name: this.restuarant.name,
                address: this.restuarant.address,
                contact: this.restuarant.contact,
            });
            console.warn(result);
            if (result.status == 201) {
                this.$router.push({
                    name: 'Home'
                })
            }
        }
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({
                name: 'SignUp'
            })
        }
    }
}
</script>

<style>

</style>
