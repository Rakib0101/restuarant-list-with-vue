<template>
  <header class="border-b pb-2">
    <div class=" container mx-auto flex justify-between items-center">
        <div class="logo">
            <img src="../assets/logo.jpg" alt="" class="w-16">
        </div>
        <div class="nav">
            <ul class="flex">
                <li class="px-1">
                    <router-link to='/' active-class="bg-red-200" class="px-2 py-1 hover:bg-red-200 cursor-pointer">Home</router-link>
                </li>
                <li class="px-1">
                    <router-link to="/about" active-class="bg-red-200" class="px-2 py-1 hover:bg-red-200 cursor-pointer">About</router-link>
                </li>
                <li class="px-1">
                    <router-link to='/add-restuarant' active-class="bg-red-200" class="px-2 py-1 hover:bg-red-200 cursor-pointer">Add Restuarant</router-link>
                </li>
                <li class="px-1">
                    <router-link to='/update-restuarant' active-class="bg-red-200" class="px-2 py-1 hover:bg-red-200 cursor-pointer">Update Restuarant</router-link>
                </li>
                <li>
                    <a class="px-2 py-1 hover:bg-red-200 cursor-pointer" v-on:click="logout">Logout</a>
                </li>
            </ul>
        </div>
    </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    methods:{
        logout(){
            localStorage.clear()
            this.$router.push({name: 'Login'})
        }
    }
}
</script>

<style>

</style>
