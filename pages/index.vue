<template>
  <Head>
    <Title>ASRCFederal</Title>
  </Head>
  <div>
    <FrontPage />
  </div>
</template>
<script setup>
import FrontPage from "./FrontPage.vue";
import "./index.css"
onMounted(() => {
  //this can be removed once we implement the page
  // window.location.href = "/";
});
</script>
