<template>
  <div id="navholder" :mnav-active="mnavActive">
    <div id="navbar" class="navbar">
      <router-link to="/"><img src="../assets/images/logo4.png" class="navlogo" /></router-link> 
      <div>
        <router-link to="/contact" class="navbtn">Contact Us</router-link>
        <div class="dropdown">
          <span style="cursor: default;" class="navbtn">Our Story</span>
          <div class="dropdown-content">

            <router-link to="/our-team" class="mnav-item">Our Team</router-link>
            <router-link to="/about" class="mnav-item">About Us</router-link>
            <router-link to="/our-mission" class="mnav-item"
              >Our Mission</router-link
            >
            <router-link to="/our-initiatives" class="mnav-item"
              >Our Initiatives</router-link
            >
          </div>
        </div>
        <div class="dropdown">
          <span style="cursor: default;" class="navbtn">Our Work</span>
          <div class="dropdown-content">
            <router-link to="/programmes/centre-model" class="mnav-item"
              >Yasham Centre Model</router-link
            >
            <router-link to="/programmes/saathi-haath-badhana" class="mnav-item"
              >Saathi Haath Badhana</router-link
            >
            <router-link to="/programmes/sunn-zara" class="mnav-item"
              >Sunn Zara</router-link
            >
            <router-link to="/programmes/hum-honge-kamyab" class="mnav-item"
              >Hum Honge Kaamyab</router-link
            >
            <router-link to="/programmes/swachh-english-mission" class="mnav-item"
              >Swacch English Mission</router-link
            >
          </div>
        </div>
        <div class="dropdown">
          <span style="cursor: default;" class="navbtn">Our Impact</span>
          <div class="dropdown-content">
            <router-link to="/student-testimonials" class="mnav-item"
              >Student Testimonials</router-link
            >
            <router-link to="/mentor-testimonials" class="mnav-item"
              >Mentor Testimonials</router-link
            >
            <router-link to="/our-impact" class="mnav-item"
              >Yasham in News</router-link
            >
          </div>
        </div>
        <div class="dropdown">
          <span style="cursor: default;" class="navbtn">Get Involved</span>
          <div class="dropdown-content">
            <router-link to="/maintenance" class="mnav-item">
              Sponsor
            </router-link>
            <router-link to="/support-us" class="mnav-item"
              >Support Us</router-link
            >
            <router-link to="/maintenance" class="mnav-item"
              >Volunteer & Intern</router-link
            >
            <router-link to="/maintenance" class="mnav-item">Teach</router-link>
            <router-link to="/maintenance" class="mnav-item">Mentor</router-link>
          </div>
        </div>
      </div>
      <a class="mnavbtn" @click="toggleNav">
        <i
          :class="
            mnavActive ? 'fas fa-times icon fa-xs' : 'fas fa-bars icon fa-xs'
          "
        ></i>
      </a>
    </div>
    <div id="mnav">
     
      <div class="dropdown" v-for="(section, index) in sections" :key="index">
        <span class="mnav-item" @click="toggleDropdown(section.name)">
          {{ section.name }} <i class="fas fa-chevron-down"></i>
        </span>
        <div
          class="dropdown-content"
          :class="{ active: activeDropdown === section.name }"
        >
          <router-link
            v-for="(link, idx) in section.links"
            :key="idx"
            :to="link.route"
            class="mnav-item2"
          >
            {{ link.label }}
          </router-link>
        </div>
      </div>
      <router-link to="/contact" class="mnav-item">Contact Us</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {
      mnavActive: false,
      activeDropdown: null,
      sections: [
        {
          name: "Our Story",
          links: [
            { label: "Our Team", route: "/our-team" },
            { label: "Our Mission", route: "/our-mission" },
            {label: "About  Us", route: "/about"},
            {label: "Our Initiatives", route: "/our-initiatives"}
          ],
        },
        {
          name: "Our Work",
          links: [
            { label: "Yasham Centre Model", route: "/programmes/centre-model" },
            { label: "Saathi Haath Badhana", route: "/programmes/saathi-haath-badhana" },
            { label: "Sunn Zara", route: "/programmes/sunn-zara" },
            { label: "Hum Honge Kaamyab", route: "/programmes/hum-honge-kamyab" },
            {
              label: "Swacch English Mission",
              route: "/programmes/swachh-english-mission",
            },
          ],
        },
        {
          name: "Our Impact",
          links: [
            { label: "Student Testimonials", route: "/student-testimonials" },
            { label: "Mentor Testimonials", route: "/student-testimonials" },
            { label: "Yasham in News", route: "/our-impact" },
          ],
        },
        {
          name: "Get Involved",
          links: [
            { label: "Sponsor", route: "/maintenance" },
            { label: "Support Us", route: "/support-us" },
            { label: "Teach", route: "/maintenance" },
            { label: "Mentor", route: "/maintenance" },
          ],
        },
      ],
    };
  },
  methods: {
    toggleNav() {
      this.mnavActive = !this.mnavActive;
    },
    toggleDropdown(sectionName) {
      this.activeDropdown =
        this.activeDropdown === sectionName ? null : sectionName;
    },
  },
};
</script>

<style scoped>
/* Add your scoped styles here */

#navholder {
  z-index: 20;
}

#navbar {
  width: 100%;
  height: 84px;
  background: #fff;
  padding: 0px 96px;
  transition: all 0.25s;
  z-index: 20;
  display: flex;
  justify-content: space-around;
  align-items: center;
  position:fixed;
  top: 0;
}

.navlogo {
  height: 130px;
  width: 125px;
  float: left;
  z-index:999;
  background-color: white;
  margin-top:5px;
  border-radius: 10%;
  padding:3px;
  padding-top: 25px;
  padding-bottom: 5px;
}

.mnavbtn {
  font-size: 2rem;
  font-weight: 600;
  line-height: 60px;
  float: right;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  color: var(--color-primary);
}

.icon {
  color: var(--color-primary);
}

#mnav {
  position: absolute;
 
  width: 100%;
  background: #fff;
  transform: scaleY(0);
  transition: all 0.25s;
  transform-origin: 0px 0px;
  display: none;
  z-index: 30;
}

.mnav-item {
  width: 100%;
  padding: 24px 32px;
  display: block;
  text-align: center;
  font-size: 14px;
  font-weight: 500;
  color: rgba(0, 0, 0, 0.8);
  border-top: solid #00000010 1px;
  cursor: pointer;
  transition: all 0.25s;
  background-color: #fff;
  z-index: 2;
}
.mnav-item2 {
  width: 100%;
  padding: 24px 32px;
  display: block;
  text-align: center;
  font-size: 14px;
  font-weight: 500;
  color:black;
  border-top: solid #00000010 1px;
  cursor: pointer;
  transition: all 0.25s;
  background-color: rgb(255, 250, 245);
  z-index: 2;
}

.mnav-item:hover {
  color: var(--color-primary);
  background:white;
}

.mnav-item:active {
  color: var(--color-primary);
  background: #f76f0220;
}

.navbtn {
  height: 60px;
  line-height: 60px;
  padding: 0px 16px;
  float: right;
  font-size: 14px;
  font-weight: 600;
  color: rgba(0, 0, 0, 0.7);
  cursor: pointer;
  text-decoration: none;
  transition: all 0.25s;
  text-align: end;
  user-select: none;
  
}

.navbtn::after {
  background: var(--color-primary);
  content: " ";
  display: block;
  width: 100%;
  height: 4px;
  margin-top: -2px;
  border-radius: 2px;
  transform: scaleX(0);
  transition: transform 0.25s;
}
.navbtn:hover::after {
  transform: scaleX(0.95);
}

.navbtn:active::after {
  transform: scaleX(0.6);
}

.navbtn[selected] {
  color: var(--color-primary);
}
.navbtn[selected]::after {
  transform: scaleX(1);
}

.navbtn[selected]:active::after {
  transform: scaleX(0.8);
}

.navbtn:hover {
  color: var(--color-primary);
  background: #f76f020b;
}

.navbtn:active {
  background: #f76f0220;
}

@media screen and (max-width: 960px) {
  #navbar {
    padding: 0px 32px;
    position: relative;
    height: 40px;
    z-index: 1000;
  }
}

@media screen and (max-width: 840px) {
  #navbar {
    padding: 0px 0px;
  }
  .navbtn {
    display: none;
  }
  .mnavbtn {
    display: block;
    position: absolute;
    align-self: center;
    right: 10px;
  }

  #mnav {
    display: block;
  }

  #navholder[mnav-active="true"] #mnav {
    transform: scaleY(1);
  }

  #navholder[mnav-active="false"] #mnav {
    transform: scaleY(0);
  }

  .navlogo{
    height: 100px;
    width: 100px;
    
    padding-top:0px;
    margin-left:25px;
  }
}
#navholder {
  position: relative;
  z-index: 20;
}

#navbar {
  width: 100%;
  height: 60px;
  background: #fff;
  padding: 0px 96px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.navbtn {
  font-size: 14px;
  font-weight: 600;
  color: rgba(0, 0, 0, 0.7);
  cursor: pointer;
  text-decoration: none;
  transition: all 0.25s;
}

.dropdown {
  position: relative;
  display: inline-block;
  border-radius: 30px;
}

.dropdown-content {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  min-width: 160px;
  /* border-bottom: 1px solid black; */
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  overflow:clip;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 998; /* Ensure dropdown is above other elements */
}
.dropdown-content span,
.dropdown-content a {
  display: block;
  padding: 12px 16px;
  text-decoration: none;
  color: rgba(0, 0, 0, 0.8);
}

.dropdown-content span:hover,
.dropdown-content a:hover {
  /* background-color: #f76f020b; */
  color: var(--color-primary);
}

.dropdown:hover .dropdown-content {
  display: block;
}

.mnavbtn {
  display: none;
}

@media screen and (max-width: 840px) {
  #navbar {
    padding: 0;
    flex-direction: column;
    align-items: flex-start;
  }

  .navbtn {
    display: none;
  }

  .mnavbtn {
    display: block;
    margin-right: 16px;
  }

  .dropdown {
    width: 100%;
  }

  .dropdown-content {
    top: auto;
    left: 0;
    right: 0;

  }

  .dropdown:hover .dropdown-content {
    display: none;
  }

  .dropdown:hover .dropdown-content.active {
    display: block;
  }
}
</style>
