<template>
<div>
    <div class="logo">
        <img class="mx-auto" src="../assets/logo.jpg" alt="" style="width:120px;">
    </div>
    <h3 class="text-4xl my-4">Sign Up</h3>
    <div class="register-form w-1/3 mx-auto border-2 border-green-500 rounded shadow-md p-12">
        <label for="name" class="block text-left">User Name :</label>
        <input class="block border rounded-sm w-full mb-2 p-1" type="text" id="name" v-model="name" placeholder="Enter Your Name">
        <label for="email" class="block text-left">Email :</label>
        <input class="block border rounded-sm w-full mb-2 p-1" type="email" id="email" v-model="email" placeholder="Enter Your Email Address">
        <label for="password" class="block text-left">Password :</label>
        <input class="block border rounded-sm w-full mb-2 p-1" type="password" id="password" v-model="password" placeholder="Enter Password">
        <button class="text-left border rounded bg-green-500 text-white px-2 py-1" v-on:click="signUp">Sign Up</button>
        <div class="mt-4">
            <span>Already have an account ? </span><router-link to="/login" class="text-blue-700">Login</router-link>
        </div>
    </div>
</div>
</template>

<script>
import axios from "axios";
export default {
    name: "SignUp",
    data() {
        return {
            name: "",
            email: "",
            password: "",
        };
    },
    methods: {
        async signUp() {
            console.warn("signUp", this.name, this.email, this.password);

            let result = await axios.post("http://localhost:3000/users", {
                name: this.name,
                email: this.email,
                password: this.password,
            });
            console.warn(result);
            if (result.status == 201) {
                localStorage.setItem("user-info", JSON.stringify(result.data));
                this.$router.push({
                    name: 'Home'
                })
            }

        },
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if (user) {
            this.$router.push({
                name: 'Home'
            })
        }
    }
};
</script>

<style>

</style>
