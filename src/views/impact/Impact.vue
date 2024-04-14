<template>
    <div class="route-page">
        <NavBar selecteditem="impact" />
        
        <div class="subsection subsection-head mob-center top">
            <h1><i class="fa fa-newspaper " style="padding-right: 16px;"></i>Yasham in the News </h1>
            <span class="underbar"></span>
        </div>

        <div class="subsection mob-center" style="background: #F5F5F5;">
            <div class="subsection mob-center" style="background: #FFFFFF;">
            
            <div class="cards-holder">
                <div style="width: 100%; display: flex; flex-direction: column; justify-content: center; align-items: center; font-size: 20px; font-weight: 500">
                    <news-carousel></news-carousel>
                </div>
            </div>
        </div>
        </div>
        

        <WaveDivider position="bottom" foreground="#FFFFFF" background="#F5F5F5" />
        
        <Footer />
    </div>
</template>

<script>
    import NavBar from '@/components/NavBar.vue'
    import Footer from '@/components/Footer.vue'
    import WaveDivider from '@/components/WaveDivider.vue'
    
    import NewsCarousel from './NewsCarousel.vue'

    export default {
        components: {
            NavBar,
            Footer,
            WaveDivider,
            
                NewsCarousel
        }
    }
</script>

<style>
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