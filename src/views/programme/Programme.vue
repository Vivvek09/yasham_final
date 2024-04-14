<template>
  <div class="route-page">
    <NavBar />

    <div
      style="
        background: var(--color-gradient) !important;
        padding-top: 5px !important;
      "
      class="top subsection subsection-head mob-center"
    >
      <h1>{{ programme.title }}</h1>
      <span class="underbar"></span>
      <p v-if="programme.subTitle">{{ programme.subTitle }}</p>
    </div>

    <PhotoGallery :images="images" />
    <!-- <WaveDivider
      position="bottom"
      foreground="#FFF"
      background="transparent"
    /> -->
    <div class="subsection mob-center slide-in-left" style="background: #fff">
      <p id="md-holder" style="line-height: 28px" v-html="contentHtml"></p>
      <!-- <SanityBlocks :blocks="[]" /> -->
    </div>

    <Footer />
  </div>
</template>

<script>
import Footer from "@/components/Footer.vue";
import PhotoGallery from "../../components/PhotoGallery.vue";
import client from "../../client";
import imageUrlBuilder from "@sanity/image-url";
import NavBar from "../../components/NavBar.vue";

const imageBuilder = imageUrlBuilder(client);

export default {
  components: {
    Footer,
    PhotoGallery,
    NavBar,
  },
  data() {
    return {
      blocks: [],
      images: [],
      programme: {},
      contentHtml: ""
    };
  },
  async mounted() {
    await this.fetchProgrammeData(this.$route.params.programmeId);
  },
  beforeRouteUpdate(to, from, next) {
    // Fetch new data when route changes
    this.fetchProgrammeData(to.params.programmeId);
    next();
  },
  methods: {
    async fetchProgrammeData(programmeId) {
      const query = `*[_type == "post" && slug.current == '${programmeId}']`;
      try {
        const programme = await client.fetch(query);
        this.programme = programme[0] || {};
        this.contentHtml = this.programme.body || "";
        this.images = (this.programme.photoGallery || []).map(e => this.imageUrlFor(e));
      } catch (error) {
        console.error('Error fetching programme data:', error);
      }
    },
    imageUrlFor(source) {
      return imageBuilder.image(source);
    },
    navigateToProgramme(programmeId) {
      const url = `/programmes/${programmeId}`;
      if (this.isMobileDevice()) {
        window.location.href = url;
      } else {
        this.$router.push(url);
      }
    },
    isMobileDevice() {
      return /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent);
    }
  }
};
</script>

<style scoped>
.parallax-bg {
  width: 100%;
  height: 100vh;
  position: fixed;
  z-index: -1;
  object-fit: cover;
  object-position: center;
  top: 0;
  transform: scale(1);
}
.top{
    margin-top: 60px;
  }

.cards-holder {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.mcard {
  margin: 16px 16px 0px 0px;
  flex-grow: 1;
  max-width: calc(50% - 16px);
}

@media screen and (max-width: 840px) {
  .cards-holder {
    flex-direction: column;
    align-items: center;
  }
  .top{
    margin-top: 0px;
  }
  .mcard {
    margin: 16px 0px 0px 0px;
    max-width: 540px;
    width: 100%;
  }
}
</style>