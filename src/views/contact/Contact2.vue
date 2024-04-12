<template>
    <div class="route-page">
        <NavBar selecteditem="support" />
        
        <div class="subsection subsection-head mob-center top" style="margin-top: 60px;">
            <h1>Contact Us</h1>
            <span class="underbar"></span>
            <div style="height: 64px;"></div>
        </div>

        <WaveDivider position="top" foreground="gradient" background="#F5F5F5" />

        <div class="subsection" style="background: #F5F5F5">
                <div class="card-list-elevate">
                    

                    <div class="card-elevate" style="padding-bottom: 24px; animation: enter-bottom 0.4s backwards;">
                        <i class="fas fa-phone card-elevate-icon"></i>
                        <div class="subsection mob-center slide-in-left" style="background: #FFF; min-height: calc(100% - 84px);">
            <div class="address-holder">
                <span style="font-size: 25px; font-weight: 600;">Yasham Foundation</span><br>
                <i class="far fa-envelope" style="display: inline-block; width: 32px; color: var(--color-primary)"></i> <a class="ylink" href="mailto:info@yashamfoundation.org">yashamfoundation@gmail.com</a><br>
                <i class="fa fa-phone" style="display: inline-block; width: 32px; color: var(--color-primary)"></i> <a>+91 +91 9820373390</a><br>
                <br>
                You can also get in touch with us on our social media pages at:
                <div style="font-weight: 600; color: var(--color-primary)">
                    <a href="https://www.instagram.com/yasham_foundation/"><i class="fab fa-instagram" style="display: inline-block; width: 32px;"></i> Instagram</a><br>
                    <a href="https://www.facebook.com/101851225485402/posts/104813755189149/"><i class="fab fa-facebook" style="display: inline-block; width: 32px;"></i> Facebook</a><br>
                    <a href="https://www.linkedin.com/company/yasham-foundation"><i class="fab fa-linkedin" style="display: inline-block; width: 32px;"></i> LinkedIn</a><br>
                </div>
            </div>
        </div>
                    </p>
                    </div>
                
                </div>
            </div>
            
           

        <Footer />
    </div>
</template>

<script>
    import NavBar from '@/components/NavBar.vue'
    import Footer from '@/components/Footer.vue'
    import WaveDivider from '@/components/WaveDivider.vue'

    export default {
        components: {
            NavBar,
            Footer,
            WaveDivider,
               
        }
    }
</script>

<style>

    .address-holder{
        line-height: 28px;
    }

    .card-list-elevate{
        width: 100%;
        margin-top: -160px;
        transform: translateZ(2px);
        display: flex;
        flex-direction: row;
        justify-content: center;
    }

    .card-elevate{
        max-width: 480px;
        width: 100%;
        background: #FFF;
        min-height: 320px;
        margin: 0px 32px;
        flex-grow: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 64px 32px;
        border-radius: 8px;
    }

    .card-elevate-icon{
        font-size: 48px; 
        color: var(--color-primary);
        padding: 32px; 
        background: #fe8a0030; 
        border-radius: 50%;
    }

    .donate-field{
        display: flex;
        flex-direction: row;
        justify-content: left;
        align-items: left;
        width: 100%;
        padding: 4px 16px;
    }
    @media screen and (max-width: 960px) {
        .card-list-elevate{
            flex-direction: column;
            align-items: center;
        }

        .card-elevate{
            margin: 32px 0px;
        }
    }
</style>