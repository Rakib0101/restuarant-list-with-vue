<template>
<div>
    <Header />
    <div class="wrapper container mx-auto">
        <h2 class="text-3xl font-semibold my-8">Update Restuarant</h2>
        <form action="" class="add-form w-2/3 border-2 border-green-500 rounded shadow-md p-12">
            <label class="block text-left" for="name">Restuarant Name:</label>
            <input class="block border rounded-sm w-full mb-2 p-1" type="text" id="name" placeholder="enter restuarant name" v-model="restuarant.name">
            <label class="block text-left" for="address">Restuarant Address:</label>
            <input class="block border rounded-sm w-full mb-2 p-1" type="text" id="address" placeholder="enter restuarant address" v-model="restuarant.address">
            <label class="block text-left" for="contact">Contact Number:</label>
            <input class="block border rounded-sm w-full mb-2 p-1" type="text" id="contact" placeholder="enter contact number" v-model="restuarant.contact">
            <button type="button" class="border rounded bg-green-500 text-white px-2 py-1" v-on:click="updateRestuarant">Update Restuarant</button>
        </form>
    </div>
</div>
</template>

<script>
import axios from 'axios'
import Header from './Header.vue'
export default {
    name: "Update",
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
        async updateRestuarant(){
            let result = await axios.put("http://localhost:3000/restuarants/"+this.$route.params.id, {
                name: this.restuarant.name,
                address: this.restuarant.address,
                contact: this.restuarant.contact,
            });
            if (result.status == 200) {
                this.$router.push({
                    name: 'Home'
                })
            }
        }
    },
    async mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({
                name: 'SignUp'
            })
        }

        const result = await axios.get("http://localhost:3000/restuarants/"+this.$route.params.id)
        this.restuarant = result.data
    }
}
</script>

<style>

</style>
