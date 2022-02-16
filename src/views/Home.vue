<template>
  <div>
    <header-shayna/>
    <hero-shayna/>
    <woman-shayna/>
    <insta-shayna/>
    <partner-shayna/>
    <footer-shayna/>
  </div>
</template>

<script>
import FooterShayna from '../components/FooterShayna.vue';
// @ is an alias to /src
import HeaderShayna from '../components/HeaderShayna.vue';
import HeroShayna from '../components/HeroShayna.vue';
import InstaShayna from '../components/InstaShayna.vue';
import PartnerShayna from '../components/PartnerShayna.vue';
import WomanShayna from '../components/WomanShayna.vue';

export default {
  name: "Home",
  components: {
    HeaderShayna,
    HeroShayna,
    WomanShayna,
    InstaShayna,
    PartnerShayna,
    FooterShayna,
  },
};
</script>
