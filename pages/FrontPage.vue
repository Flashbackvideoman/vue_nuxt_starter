<template>
  <AppLeftNav />
  <div id="FrontPage" class="full-height">
    <div class="titleText">Nextgen Water Prediction</div>
    <div id="SampleChart">
      Sample Chart:
      <div>
        <SampleChart />
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import "@/components/AppLeftNav.vue";
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

#SampleChart {
  width: 50%;
  margin: 0 auto;
  margin-top: 100px;
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
