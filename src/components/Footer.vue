<template>
  <footer>
    <div class="footer-main">
      <div class="footer-nav">
        <img
          class="footer-logo-mobile"
          src="../assets/img/cafeynLogo.svg"
          alt="cafeyn logo"
        />
        <a class="footer-logo" href="https://www.cafeyn.co/fr/newsstand">
          <img src="../assets/img/cafeyn.svg" alt="logo cafeyn" />
        </a>
        <div
          class="footer-nav-categories"
          v-for="{ title, categories } in navCategoriesFooter"
          :key="title"
        >
          <h2 class="footer-nav-titles">{{ title }}</h2>
          <ul>
            <li v-for="categorie in categories" :key="categorie">
              <div class="footer-nav-categorie">{{ categorie }}</div>
            </li>
          </ul>
        </div>
      </div>

      <div class="footer-icons">
        <div>
          <div class="footer-app-redirect">
            <a
              href="https://apps.apple.com/fr/app/lekiosk-digital-newsstand/id626703984?l=fr"
            >
              <img
                src="https://cscdouessin.centres-sociaux.fr/files/2020/05/Logo-App-Store.png"
                alt="logo-available-apple"
              />
            </a>
            <a
              href="https://play.google.com/store/apps/details?id=fr.lekiosque&hl=fr"
            >
              <img
                src="https://upload.wikimedia.org/wikipedia/commons/a/ab/Logo_Google_play.jpg"
                alt="logo-available-google"
                :style="{ marginLeft: '25px' }"
              />
            </a>
          </div>
          <div class="footer-social-icons">
            <p class="footer-social-follow">Suivez nous</p>
            <a
              class="footer-social-icon"
              href="https://apps.apple.com/fr/app/lekiosk-digital-newsstand/id626703984?l=fr"
            >
              <FaFacebookF />
            </a>
            <a
              class="footer-social-icon"
              href="https://apps.apple.com/fr/app/lekiosk-digital-newsstand/id626703984?l=fr"
            >
              <AiFillInstagram />
            </a>
            <a
              class="footer-social-icon"
              href="https://apps.apple.com/fr/app/lekiosk-digital-newsstand/id626703984?l=fr"
            >
              <FaTwitter />
            </a>
          </div>
        </div>
      </div>
    </div>
    <div class="footer-mentions">
      <div class="footer-left">
        <div class="footer-left-languages">
          <div class="footer-left-languages-visible">
            <span class="footer-left-language-chosen">
              {{ languages[0] }}
              <span class="footer-left-language-chosen-icon">
                <BiChevronDown />
              </span>
            </span>
          </div>

          <div class="footer-left-languages-store">
            <div
              v-for="language in languages.filter((l) => l !== '🇫🇷 France')"
              :key="language"
              :class="{
                'footer-left-language': true,
                top: this.checkIndex(language),
              }"
            >
              {{ language }}
            </div>
          </div>
        </div>
        <a
          class="footer-left-item"
          href="https://cdn1.lekiosk.com/Public/Cafeyn/pdfs/legal/fr/legal_lkios.pdf"
        >
          Conditions d'utilisation et de vente
        </a>
        <a
          class="footer-left-item"
          href="https://cdn1.lekiosk.com/Public/Cafeyn/pdfs/legal/fr/privacypolicy_lkios.pdf"
        >
          Politique de confidentialité
        </a>
      </div>
      <p>© 2021 - Tous droits réservés Lekiosque.fr</p>
    </div>
  </footer>
</template>

<script>
import { navCategoriesFooter, languages } from "../assets/cafeyn.fixtures";

export default {
  name: "Footer",
  data() {
    return {
      navCategoriesFooter,
      languages: languages,
    };
  },
  methods: {
    checkIndex(lang) {
      return languages.indexOf(lang) % 2;
    },
  },
};
</script>

<style>
footer {
  background-color: var(--cafeyn-bcg-color);
  border-top: 1px solid var(--cafeyn-border-color);
  position: relative;
  z-index: 0;
}

.footer-app-redirect > a > img {
  height: 43px;
  width: 124px;
}

.footer-icons {
  align-items: flex-start;
  display: flex;
  flex-wrap: nowrap;
  justify-content: flex-end;
  margin-top: 0;
  padding: 75px 0 0 0;
  width: 35%;
}

.footer-icons > div {
  text-align: center;
}

.footer-left {
  align-items: center;
  display: flex;
  justify-content: flex-start;
  flex-wrap: nowrap;
  padding-left: 34px;
}

.footer-left-item {
  font-size: 14px;
  margin: 0 10px;
}

.footer-left > a {
  color: #bec2c5;
  letter-spacing: -0.0125rem;
  line-height: 1.375rem;
  font-family: Soleil, Helvetica, sans-serif;
  font-style: normal;
  font-weight: 400;
}

.footer-left-language {
  color: #536067;
  border: 1px solid #bec2c5;
  font-size: 14px;
  line-height: 1.375rem;
  padding: 3px 11px;
}

.footer-left-language.top {
  border-bottom: none;
}

.footer-left-language-chosen {
  color: #536067;
  font-size: 0.875rem;
  line-height: 1.375rem;
  position: relative;
}
.footer-left-language-chosen {
  color: #536067;
  font-size: 0.875rem;
  line-height: 1.375rem;
  position: relative;
}

.footer-left-language-chosen-icon {
  position: absolute;
  right: -17px;
  top: 3px;
}

.footer-left-language-chosen:hover > .footer-left-language-chosen-icon {
  top: 0px;
  transform: rotate(-180deg);
  transition: all 0.5s ease-out;
}

.footer-left-languages {
  position: relative;
  cursor: pointer;
  display: inline-block;
}

.footer-left-languages-store {
  left: -12px;
  opacity: 0;
  position: absolute;
  text-align: left;
  top: -71px;
  transform: translateY(20px);
  transition: all 0.5s ease-out;
  visibility: hidden;
  width: 150px;
}

.footer-left-languages:hover > .footer-left-languages-store {
  background-color: var(--cafeyn-bcg-color);
  opacity: 1;
  transform: translateY(0);
  visibility: visible;
}

.footer-left-languages-visible {
  align-items: center;
  display: flex;
  margin-right: 23px;
}

.footer-logo {
  margin-bottom: 65px;
  margin-right: 4%;
  width: auto;
}
.footer-logo > img {
  display: block;
  position: relative;
  width: 113px;
}

.footer-logo-mobile {
  display: none;
}

.footer-main {
  display: flex;
  margin: auto;
  max-width: 1224px;
}
.footer-mentions {
  align-items: center;
  border-top: 1px solid var(--cafeyn-border-color);
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin: 0;
  padding: 7px 0;
  text-align: center;
}

.footer-mentions > p {
  color: #bec2c5;
  font-size: 14px;
  line-height: 1.375rem;
  letter-spacing: -0.0125rem;
  margin-right: 33px;
}

.footer-nav {
  align-items: flex-start;
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  padding: 75px 0 55px 0;
  width: 65%;
}

.footer-nav-categories {
  display: flex;
  flex-direction: column;
}

.footer-nav-categories > ul {
  list-style: none;
  margin-bottom: 10px;
  padding: 0;
}

.footer-nav-categorie {
  color: var(--cafeyn-grey-color);
  letter-spacing: -0.0125rem;
  line-height: 2.375rem;
  font-family: Soleil, Helvetica, sans-serif;
  font-size: 0.98rem;
  font-style: normal;
  font-weight: 400;
}

.footer-nav-categorie:hover {
  color: #1e323d;
}

.footer-nav-titles {
  color: #1e323d;
  border-bottom: none;
  display: block;
  font-size: 1.08rem;
  letter-spacing: -0.0375rem;
  font-family: Soleil, Helvetica, sans-serif;
  font-style: normal;
  font-weight: 400;
  margin-bottom: 8px;
  padding: 0 0;
  position: relative;
  width: auto;
}

.footer-social-icons {
  display: inline-block;
  margin-top: 50px;
  text-align: center;
}

.footer-social-icon {
  background-color: var(--cafeyn-bcg-color);
  border: 1px solid var(--cafeyn-border-color);
  border-radius: 27px;
  color: #1e323d;
  display: inline-block;
  font-size: 19px;
  height: 54px;
  line-height: 3.5rem;
  margin: 0 8px;
  padding: 0px;
  text-decoration: none;
  width: 54px;
}

.footer-social-follow {
  color: #86949b;
  letter-spacing: 0.05rem;
  line-height: 1.125rem;
  font-family: Soleil-bold, Helvetica, sans-serif;
  font-size: 0.75rem;
  font-style: normal;
  font-weight: 400;
  margin-bottom: 15px;
  text-transform: uppercase;
}

@media screen and (max-width: 1023px) {
  .footer-icons {
    align-items: center;
    justify-content: center;
    margin-bottom: 50px;
    width: 100%;
  }

  .footer-logo {
    display: none;
  }

  .footer-logo-mobile {
    background-color: white;
    display: block;
    height: 44px;
    left: calc(50% - 15px);
    position: absolute;
    top: -23px;
  }

  .footer-main {
    align-items: center;
    flex-direction: column;
  }
  .footer-mentions {
    justify-content: center;
    padding-top: 25px;
  }
}

@media screen and (min-width: 768px) and (max-width: 1023px) {
  .footer-app-redirect {
    display: flex;
  }
}

@media screen and (max-width: 767px) {
  .footer-left {
    flex-direction: column;
    height: 85px;
    justify-content: space-between;
  }

  .footer-mentions > p {
    margin-right: 0;
  }

  .footer-nav {
    flex-direction: column;
    width: 80%;
  }

  .footer-nav-categories {
    width: 100%;
  }

  .footer-nav-titles {
    border-bottom: 1px solid #f1efef;
    padding-bottom: 10px;
    width: 100%;
  }
}
</style>
