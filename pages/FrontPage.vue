<template>
  <AppLeftNav />
  <div id="FrontPage" class="full-height">
    <div class="titleText">ASRCFederal Water Model Information Front Page</div>
  </div>
</template>
<script lang="ts">
import "@/components/AppLeftNav.vue"
export default {
  name: "FrontPage",
  data: () => ({
    inputType: "Name",
    displayCesium: true,
  }),
  methods: {
    submitReport() {
      alert("Report submitted");
    },
  },
};
</script>
<style lang="scss">
html,
body {
  overflow: hidden;
  height: 100%;
}

.full-height {
  height: 100%;
}
.titleText {
  padding: 50px 0 0 100px;
  font-size: 40px;
}
#FrontPage {
  height: 1024px;
  color: white;

}
</style>
