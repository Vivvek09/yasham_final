<template>
    <div class="route-page">
        <NavBar selecteditem="support" />
           <div style="display: flex; background: var(--color-gradient); justify-content: center; align-items: center; height: 80vh; margin-top: 60px; margin-bottom: 10px;">
        <div class="maintenance">
        <h2>Sorry, the page is currently <br>under <span style="color: #f76f02">Construction</span></h2>
        <!-- <br> -->
        <h3><span style="color: #f76f02">Email:</span> yashamfoundation@gmail.com</h3>
        <!-- <br> -->
        <h3><span style="color: #f76f02">Message Us/Whatsapp:<br></span> +91-9820373390</h3>
        </div>
    </div>

        <Footer />
    </div>
</template>

<script>
    import NavBar from '@/components/NavBar.vue'
    import Footer from '@/components/Footer.vue'
    

    export default {
        components: {
            NavBar,
            Footer,
        }
    }
</script>

<style>
   
   .maintenance {
    
    color: black;

    text-align: center;
    
    line-height: 30px;
    background-color: whitesmoke;
    box-shadow: 0px 3px 10px 1px rgb(44, 44, 44);
    border-radius: 5px;
    font-weight: 700;
    padding: 10px;
}
</style>