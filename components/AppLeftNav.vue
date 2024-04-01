<template>
  <div id="left-nav">
    <div
      id="slide-out"
      name="slide-out"
      :class="{ 'full-size': isFullSize }"
      @click="
        {
          isFullSize = !isFullSize;
        }
      ">
      <nav aria-label="Navigation menu">
        <div class="navitem">
          <div class="navitem-icon">
            <em class="pi pi-user" />
          </div>
          User Name
          <div class="navitem-icon" />
          <a id="logout" href="#">Log Off</a>
        </div>
        <hr />
        <NuxtLink id="home" class="navitem" to="/">
          <div class="navitem-icon">
            <em class="pi pi-th-large" />
          </div>
          Home
        </NuxtLink>
        <NuxtLink id="Page1" class="navitem" to="/">
          <div class="navitem-icon">
            <img src="@/assets/styles/img/asrc.png" alt="Page1" width="35" />
          </div>
          Page1
        </NuxtLink>
        <NuxtLink id="Page2" class="navitem" to="/">
          <div class="navitem-icon">
            <img src="@/assets/styles/img/asrc.png" alt="Page2" width="35" />
          </div>
          Page2
        </NuxtLink>
        <NuxtLink id="Page3" class="navitem" to="/">
          <div class="navitem-icon">
            <img src="@/assets/styles/img/asrc.png" alt="Page3" width="35" />
          </div>
          Page3
        </NuxtLink>
        <hr />
        <NuxtLink id="help" class="navitem" to="/" target="_blank">
          <div class="navitem-icon">
            <em class="pi pi-question-circle" />
          </div>
          Help
        </NuxtLink>
      </nav>
    </div>

    <!-- Mobile Drop Down Menu -->
    <div id="mobileMenuLink" @click="openMobileMenu">
      <em class="pi pi-list" style="font-size: 1em" />
    </div>
    <div id="slide-down" name="slide-down">
      <nav id="slide-down-nav" ref="slideDownNav" aria-label="Mobile Navigation menu">
        <br />
        <div class="navitem">
          <div class="navitem-icon">
            <em class="bi pi pi-user" />&nbsp;Welcome
            <br />
            Sally Operator
          </div>
          <div class="navitem-icon" />
          <a href="#">&nbsp;Log off</a>
        </div>
        <hr />
        <NuxtLink id="home" class="navitem" to="/">
          <div class="navitem-icon">
            <em class="pi pi-th-large" />
            Home
          </div>
        </NuxtLink>
        <NuxtLink id="pgmMain" class="navitem" to="/">
          <div class="navitem-icon">
           <em class="pi pi-question-circle" />
            ESAA
          </div>
        </NuxtLink>
        <NuxtLink id="productReports" class="navitem" to="/">
          <div class="navitem-icon">
            <em class="pi pi-question-circle" />
            Product Reports
          </div>
        </NuxtLink>
        <NuxtLink id="dataIngestionMonitor" class="navitem" to="/">
          <div class="navitem-icon">
            <!-- <img src="@/assets/styles/img/data-ingestion-icon.svg" alt="Data ingestion icon" width="20" height="21" /> -->
            Data Ingestion
          </div>
        </NuxtLink>
        <hr />
        <NuxtLink id="help" lass="navitem" to="/" target="_blank">
          <div class="navitem-icon">
            <em class="pi pi-question-circle" />
            Help
          </div>
        </NuxtLink>
      </nav>
    </div>
  </div>
</template>
<script lang="ts">
export default {
  name: "AppLeftNav",
  data: () => ({
    sdn: null,
    isFullSize: false,
  }),
  mounted() {
    this.sdn = this.$refs.slideDownNav;
    window.addEventListener("resize", this.hideDropDownOnResize);
  },
  unmounted() {
    window.removeEventListener("resize", this.hideDropDownOnResize);
  },
  methods: {
    /**
     * When the screen width < value set by
     * '@media only screen and (max-width: 600px)'
     * the side menu is hidden and the mobile menu icon appears.
     * Clicking on the mobile menu icon will animate the expanding
     * and contracting, vertically, of the menu.
     * To change the max height of the menu, change maxMenuHeight, below.
     */
    openMobileMenu() {
      const maxMenuHeight = 350;
      const elem = this.sdn;
      const h = elem.clientHeight;
      const up = !h || h === "0px" ? false : true;
      let ht = up ? maxMenuHeight : 0;
      let id = setInterval(frame, 1);
      function frame() {
        if (!up) {
          if (ht >= maxMenuHeight) {
            clearInterval(id);
          } else {
            ht = ht + 5;
            elem.style.height = ht + "px";
          }
        } else {
          if (ht <= 0) {
            clearInterval(id);
          } else {
            ht = ht - 5;
            elem.style.height = ht + "px";
          }
        }
      }
    },
    hideDropDownOnResize() {
      this.sdn.style.height = "0px";
    },
  },
};
</script>
<style lang="scss" scoped>
// Scss Document

@import "@/assets/styles/styles.scss";

body {
  background-color: #000017 !important;
  color: #d9d9d9 !important;
  font-family: Roboto, Arial, Helvetica, sans-serif !important;
  font-size: 16px !important;
  line-height: 1.4rem !important;
  display: flex;
  flex-direction: column;
  overflow-y: scroll !important;
}

// unvisited link
a,
a:link {
  color: $light;
  text-decoration: none;
  border-bottom: 1px dotted $gray-50;
  padding-bottom: 1px;
}

// visited link 
a:visited {
  color: $light;
  text-decoration: none;
  border-bottom: 1px dotted $gray-70;
  padding-bottom: 1px;
}

// mouse over link 
a:hover {
  color: $white;
  text-decoration: none;
  border-bottom: 1px solid $white;
  padding-bottom: 1px;
}

 //selected link 
a:active {
  color: $white;
  text-decoration: none;
  border-bottom: 1px solid $white;
  padding-bottom: 1px;
}

i {
  display: inline-block;
  position: relative;
  margin-right: 0.5rem;
}

// Tabs
nav {
  padding-bottom: 15px;
}

.navitem-icon .bi {
  background-color: #172635;
  color: $light;
}
#slide-out {
  overflow: hidden;
  position: fixed;
  top: 0;
  left: 0;
  background: $dark;
  padding: 20px 0px 20px 0px;
  z-index: 2100;
  height: 100%;
  width: 50px;
  transition: width 0.25s;
  transition-timing-function: ease-in-out;
  box-shadow: 1px 0px 3px $black;
}

.full-size {
  width: 200px !important;
  transition: width 0.25s !important;
  transition-timing-function: ease-in-out !important;
}

#slide-out a.navitem {
  border: none;
  display: inline-block;
}

#slide-out .navitem {
  width: 250px;
  padding: 3px 10px 3px 0px;
  margin-bottom: 2px;
  background: linear-gradient(to right, black 50%, $dark 50%);
  background-size: 200% 100%;
  background-position: right bottom;
  transition: all 0.5s ease-out;
}

#slide-out .navitem:hover {
  background-position: left bottom;
}

#slide-out .navlabel {
  width: 250px;
  padding: 10px 10px 10px 55px;
  margin-bottom: 5px;
}

#slide-out hr {
  background: $gray-50;
  margin: 10px;
}

#slide-out .navitem .navitem-icon {
  display: inline-block;
  padding: 5px 5px 5px 12px;
  width: 55px;
  text-align: left;
}

#slide-out #logout {
  font-size: 0.9em;
  margin-left: 59px;
}

#slide-down .navitem .navitem-icon {
  padding-bottom: 10px;
}

#mobileMenuLink {
  position: fixed;
  top: 0;
  left: 0;
  width: 50px;
  text-align: center;
  background-color: $dark;
  padding: 5px 0 0 5px;
  border-radius: 0 0 10px 10px;
}

#slide-down {
  overflow: hidden;
  z-index: 1000;
  width: 180px;
  position: fixed;
  top: 25px;
  padding-left: 10px;
  padding-top: 0px;
  background-color: $dark;
  background-image: linear-gradient($background-gradient-start, $background-gradient-end);
  left: 0;
  box-shadow: 1px 0px 3px $black;
}

#slide-down nav {
  height: 0px;
  padding-bottom: 0;
}

#slide-down hr {
  background: $gray-50;
  margin: 10px;
}

@media only screen and (max-width: 600px) {
  #slide-out {
    display: none;
  }
}

@media only screen and (min-width: 600px) {
  #mobileMenuLink {
    display: none;
  }
}

</style>
