<template>
<div>
    <Header />
    <div class="wrapper container mx-auto">
        <h2 class="text-center text-4xl mt-12">Hi {{name}} ! Welcome to our website.</h2>
    </div>
</div>
</template>

<script>
import Header from './Header.vue'
export default {
    name: "Home",
    components: {
        Header
    },
    data(){
        return{
            name:''
        }
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        this.name = JSON.parse(user).name
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
