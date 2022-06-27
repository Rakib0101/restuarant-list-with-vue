<template>
<div>
    <Header />
    <div class="wrapper container mx-auto">
        <h2>This is Add Restuarant Page</h2>
    </div>
</div>
</template>

<script>
import Header from './Header.vue'
export default {
    name: "Add",
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
