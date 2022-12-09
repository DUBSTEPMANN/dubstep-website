<script>
import PageHeaderVue from './sections/PageHeader.vue';
import MissionStatementVue from './sections/MissionStatement.vue';
import PastProjects from './sections/PastProjects.vue';
import AboutMeVue from './sections/AboutMe.vue';
import FooterVue from './sections/Footer.vue';
import PricingVue from './sections/Pricing.vue';

export default {
  name: 'App',
  components: {
    PageHeaderVue,
    MissionStatementVue,
    PastProjects,
    AboutMeVue,
    FooterVue,
    PricingVue
  }
}
</script>

<template>
  <header>
    <PageHeaderVue />
  </header>

  <main>
    <div class="main-container">
      <MissionStatementVue></MissionStatementVue>
      <past-projects></past-projects>
      <AboutMeVue/>
      <PricingVue/>
    </div>
    <FooterVue/>
  </main>
</template>

<style>
#app {
  width: 100%;
}

main {
  position: absolute;
  top: 87%;
  width: 100%;
  min-height: 12%;
  z-index: 2;
  background: white;
}

.main-container {
  max-width: 1200px;
  margin: auto;
}

@media screen and (max-width: 1200px) {
  .main-container {
    padding: 0 10px;
  }
}
</style>
