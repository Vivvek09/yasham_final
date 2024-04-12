<template>
  <div class="route-page">
    <NavBar selecteditem="about" />

    <div class="subsection subsection-head mob-center top" >
      <h2>Student Testimonials</h2>
      <span class="underbar" style="background: #fff"></span><br />
      <p class="slide-in-left" style="line-height: 28px">
        Yasham works every single day to empower society holistically, through
        changes big or small. We work predominantly in the field of education to
        sharpen young minds and make them a better version of themselves,
        irrespective of where they come from.
      </p>
    </div>

    <WaveDivider position="top" foreground="gradient" background="#FFF" />
     
    <div class="testimonials" style="display: flex; flex-direction: row;padding:20px; flex-wrap: wrap; justify-content: space-around;">
 
    <div v-for="(item, index) in testList" :key="index" v-if!="item[7]" style="padding: 40px; " >
      <div style="border: 1px; border-color: aqua;  background: var(--color-gradient); border-radius: 7%;">
      <TestimonialCard :item="item"  />
  </div>
    </div>
  
</div>

    <Footer />
  </div>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
import Footer from "@/components/Footer.vue";
import WaveDivider from "@/components/WaveDivider.vue";
import TestimonialCard from "../../components/TestimonialCard.vue";
import testimonials from "@/content/testimonials.json";


import client from "../../client";
export default {
name: "Testimonials",
components: {
  TestimonialCard,
  
  WaveDivider,
  Footer,
  NavBar
},
data: function () {
  return {
    perPage: 4,
    testList: testimonials,
  };
},
computed: {
  changePerPage() {
    let width = window.innerWidth;
    if (width < 480) return 1;
    else if (width < 768) return 2;
    else return 3;
  },
},
mounted: async function () {
  const query = '*[_type == "testimonial"]';
  this.testList = await client.fetch(query);
},
};
</script>

<style>

@media screen and (max-width: 840px) {
 .subsection{
 margin-top: 0px;
 }
}
.team-holder {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 32px;
}

h3 {
  text-transform: uppercase;
}
.testimonials {
width: 100%;
overflow: hidden;
}
.VueCarousel .VueCarousel-navigation-button {
color: #f76f02;
font-size: xx-large;
top: -150px;
}
.VueCarousel-navigation-next {
right: 50px !important;
}

.VueCarousel-navigation-prev {
left: 50px !important;
margin-right: 20px;
}

.VueCarousel-wrapper {
left: 7vw;
}
@media screen and (max-width: 1000px) {
.VueCarousel-wrapper {
  left: 8vw;
}
}

@media only screen and (max-width: 600px) {
.VueCarousel-wrapper {
  text-align: center;
  left: 11vw;
}
}
</style>