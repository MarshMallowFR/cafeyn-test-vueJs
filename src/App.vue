<template>
  <Header />
  <div id="main-section">
    <Nav showHeader="{showHeader}" />
    <Section
      title="Quotidiens"
      description="L'actu très très chaud"
      :navItems="navCategoriesSection"
      @setSubCategorie="setSubCategorie"
      :subCategorie="subCategorie"
    />
    <Content :subCategorie="subCategorie" />
  </div>
  <Footer />
</template>

<script>
import Header from "@/components/Header.vue";
import Nav from "@/components/Nav.vue";
import Footer from "@/components/Footer.vue";
import Section from "@/components/Section.vue";
import Content from "@/components/Content.vue";

import { navCategoriesSection } from "@/assets/cafeyn.fixtures";

export default {
  name: "App",
  components: {
    Header,
    Nav,
    Section,
    Footer,
    Content,
  },
  data() {
    return {
      navCategoriesSection,
      subCategorie: "tout",
    };
  },
  methods: {
    setSubCategorie(cat) {
      console.log("toto", this.subCategorie);
      this.subCategorie = cat;
    },
  },
};
</script>

<style>
@font-face {
  font-family: "Soleil";
  src: url("./assets/fonts/Soleil_Regular.ttf");
}
@font-face {
  font-family: "Soleil-bold";
  src: url("./assets/fonts/Soleil_Bold.ttf");
}
@font-face {
  font-family: "Soleil-light";
  src: url("./assets/fonts/Soleil_Bold.ttf");
}

:root {
  --cafeyn-bcg-color: white;
  --cafeyn-border-color: #ececec;
  --cafeyn-grey-color: #536067;
  --cafeyn-loginRegister-color: #fedc84;
}

a {
  text-decoration: none;
}

ul {
  list-style: none;
}

#main-section {
  background-color: var(--cafeyn-bcg-color);
  margin-top: 81px;
  min-height: calc(-51px + 100vh);
}

.App-Root {
  box-sizing: border-box;
  font-family: "Soleil";
  margin: 0;
}

.hightLight-content {
  background-color: rgba(22, 23, 31, 0);
  height: 100%;
  left: 0;
  pointer-events: none;
  position: absolute;
  top: 0;
  transition: all 0.5s ease-out;
  width: 100%;
  z-index: 10000;
}

body {
  background-color: var(--cafeyn-bcg-color);
  margin: auto;
  max-width: 1274px;
}
</style>
