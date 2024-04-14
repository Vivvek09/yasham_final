<template>
    <div style="width: 100%;">
        <div class="nc-item" id="nc-animator">
            <div style=" background-color: black; border-radius: 3%; padding: 3px; padding-bottom:0px">
                <img :src="news[currentNews].image" />
            </div>
            <div class="nc-right">
                <h2>{{news[currentNews].title}}</h2>
                <span style="">
                    <span class="nc-apos">"</span>
                    {{news[currentNews].subtitle}}
                    <span class="nc-apos">"</span>
                </span>
                <p style="line-height: 28px" v-html="news[currentNews].content"></p>
                <a style="text-align: left; color:darkblue; font-weight: 700;" href="news[currentNews].href">Click here to read the Full Article</a>
            </div>
        </div>
        
        <div class="carousel-select">
            <span v-if!="" v-for="(news, index) in news" v-on:click="selectNews(index)" v-bind:key="index" v-bind:selected="currentNews==index"></span>
        </div>
    </div>
</template>

<script>
    let newsImages = [
        require('@/assets/images/mm.png'),
        require('@/assets/images/image_placeholder2.jpg'),
        require('@/assets/images/image_placeholder3bw.jpg'),
    ]


    export default {
        components: {
        },
        methods: {
            selectNews(index){
                let ncAnimator = document.getElementById("nc-animator");
                ncAnimator.classList.remove("slide-in");
                ncAnimator.classList.add("slide-out");

                setTimeout(()=>{
                    this.currentNews = index;
                    ncAnimator.classList.remove("slide-out");
                    ncAnimator.classList.add("slide-in");
                },250);
                
            },
            
        },
        data: function(){
            return {
                news: [
                    {
                        title: "MUMBAI MIRROR",
                        subtitle: "Keeping their JEE, NEET dreams alive",
                        content: `
                            Yasham Foundation has always aspired to help the youth of this nation work towards a brighter future by helping them realise their dreams.\n\nAnd the same can be said when a group of students approached our Founder, Sunita Mandelia for help with finances to enrol for JEE and NEET classes. Despite not having the funds to aid the students fully, the foundation found a way to help these bright minds.\n\nAnd help came from ‘one of the foundation’s brightest students, Shivam’. Despite preparing for JEE himself he chose to help his peers by coaching them twice a week. Since then several other professionals have joined the foundation in helping these young, driven minds in coming one step closer their goals. After all, in the words of our founder, ‘the future belongs to the youths, if we nurture them, they will be the nation’s glory.’
                            `,
                            href: `https://mumbaimirror.indiatimes.com/mumbai/other/keeping-their-jee-neet-dreams-alive/articleshow/78962390.cms`,
                        image: newsImages[0]
                    },
                    
                ],
                currentNews: 0
            }
        }
    }
</script>

<style scoped>
    .nc-item{
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 32px;
    }

    .nc-item img{
        width: 360px;
        height: 320px;
       
        object-position: center;
        border-radius: 8px;
        
    }

    .nc-item p{
        color: rgba(0, 0, 0, 0.75);
    }

    .nc-right{
        margin-left: 32px;
        font-size: 14px;
    }

    .nc-apos{
        color: var(--color-primary);
    }

    .slide-out{
        animation: slide-out 0.2s;
        animation-fill-mode: forwards;
    }

    .slide-in{
        animation: slide-in 0.2s;
        animation-fill-mode: forwards;
    }

    .fade-out{
        animation: fade-out 0.2s;
        animation-fill-mode: forwards;
    }

    .fade-in{
        animation: fade-in 0.2s;
        animation-fill-mode: forwards;
    }

    .carousel-select{
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: center;
        margin-top: 32px;
    }

    .carousel-select span{
        display: block;
        width: 12px;
        height: 12px;
        background: var(--color-primary);
        border-radius: 16px;
        margin: 0px 8px;
        opacity: 0.5;
        transform: scale(0.75);
        cursor: pointer;
        transition: all 0.25s;
    }

    .carousel-select span[selected]{
        opacity: 1;
        transform: scale(1);
    }

    

    @media screen and (max-width: 1080px) {
        .nc-item{
            flex-direction: column;
        }

        .nc-right{
            margin-top: 32px;
            margin-left: 0px;
        }
    }

    @keyframes slide-in {
        from {
            opacity: 0;
            transform: translateX(-128px);
        }
        to {
            opacity: 1;
            transform: translateX(0px);
        }
    }

    @keyframes slide-out {
        from {
            opacity: 1;
            transform: translateX(0px);
        }
        to {
            opacity: 0;
            transform: translateX(128px);
        }
    }

    @keyframes fade-in {
        from {
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }

    @keyframes fade-out {
        from {
            opacity: 1;
        }
        to {
            opacity: 0;
        }
    }
</style>