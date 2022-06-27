<template>
<div class="wrapper">
    <Header />
    <div class="container mx-auto">
        <h2>This is Update Restuarant Page</h2>
    </div>
</div>
</template>

<script>
import Header from './Header.vue'
export default {
    name: "Update",
    components: {
        Header
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
