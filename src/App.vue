<template>
  <v-app color="brown" v-scroll="onScroll">
    <v-app-bar width="100%" app dense flat :color="appBarBG" scroll-off-screen dark>
      <v-toolbar-title class="headline text-uppercase">Cocoa</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-sheet color="transparent" class="hidden-sm-and-down">
        <v-btn
          color="transparent"
          v-for="(item, index) of navList"
          :key="index"
          depressed
          exact
          @click="$vuetify.goTo(item.href, goToOptions)"
          >{{ item.title }}</v-btn
        >
      </v-sheet>
      <v-menu
        dark
        v-model="drawer"
        offset-y
        allow-overflow
        min-width="100%"
        bottom
        close-on-click
        rounded="0"
        close-on-content-click
        fixed
      >
        <template v-slot:activator="{ on, attrs }">
          <v-app-bar-nav-icon class="hidden-md-and-up" v-bind="attrs" v-on="on"></v-app-bar-nav-icon>
        </template>

        <v-list :color="appBarBG">
          <v-list-item v-for="(item, index) of navList" :key="index">
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-main class="pa-0 yellow-showad">
      <v-carousel cycle height="100vh" hide-delimiter-background show-arrows-on-hover vertical-delimiters="right">
        <v-carousel-item v-for="(item, i) of carouselList" :key="i" :src="item['background-image']" tag="div">
          <v-sheet class="d-flex justify-center align-center pa-auto transparent" height="100%">
            <v-img width="100%" max-width="600px" :src="item.src" alt />
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
      <v-sheet class="mx-auto pa-5 transparent" max-width="1000px">
        <section id="company">
          <h3 class="d-none">COMPANY</h3>
          <v-img contain class="mx-auto my-0" src="./assets/Company2.png" alt="company" width="664" height="205" />
          <v-row class="mt-5">
            <v-col cols="12" sm="6">
              <v-img src="./assets/kakao3.png" alt="kakao" width="100%" contain max-width="607" height="709" />
            </v-col>
            <v-col cols="12" sm="6">
              <h3>ABOUT US</h3>
              <p class="mt-8">
                Longmile Cocoa is a private company established by a group of young guys, who got their expertise and
                enthusiasm for cocoa and chocolate.
              </p>
              <p>
                We got the inspiration from a simple idea of making affordable but quality chocolates for people who
                consumes less tasty but cheaper confection that applies cocoa butter substitute.
              </p>
              <p>
                For production, longmile has established sophisticated production lines and systematic quality control
                measures in Shandong Province. Thus, we are widely recognized by clients for our product quality.
              </p>
              <p>
                For sales, longmile is offering very competitive price to clients. Our clients have been enjoying their
                competitiveness among their rivals. This simple sales strategy has made the business of our clients
                successful. This is how longmile’s business is growing rapidly.
              </p>
              <p class="mb-8">
                it is our firm belief that the only possible way not to be loser in business is to first make our
                clients the winners.
              </p>
              <h3>VISION</h3>
              <p class="my-8">To produce then innovate, make the benefits of cocoa accessible to the whole mankind</p>
              <h3 style="font-size: 1.1em!important; font-weight: bold;">MISSION</h3>
              <p class="mt-8">
                Optimize the quality and cost control in production and sales of cocoa powder, cocoa butter and liquor.
                Offer competitive price without compromise the product and service quality.
              </p>
              <p class="mb-8">
                Keep innovation the top strategy to bring more diversified and sophisticated Cocoa health care products,
                quality Cocoa delicacies to the whole mankind.
              </p>
            </v-col>
          </v-row>
        </section>
        <section id="products">
          <h3 class="d-none">PRODUCTS</h3>
          <v-img contain class="mx-auto my-0" src="./assets/Products1.png" alt="products" width="664" height="230" />
          <v-row>
            <v-col v-for="(product, i) of productList" :key="i" cols="6" sm="4">
              <v-card outlined hover>
                <v-img width="100%" max-height="150px" :src="product.img" />
                <h4 class="pl-4 text-h6">{{ product.name }}</h4>
                <h5 class="pl-4 text-subtitle-1">{{ product.code }}</h5>
                <v-divider></v-divider>
                <div class="pl-4" v-for="(specification, index) of product.specificationList" :key="index">
                  <div class="text-subtitle-1 font-weight-bold">{{ specification[0] }}</div>
                  <p class="body-1">{{ specification[1] }}</p>
                </div>
              </v-card>
            </v-col>
          </v-row>
        </section>
        <section id="facilities">
          <h3 class="d-none">FACILITIES</h3>
          <v-row>
            <v-col cols="12">
              <v-img class="mx-auto" contain src="./assets/Facilities2.png" alt="Facilities" width="664" height="215" />
            </v-col>
            <v-col cols="12" class="text-center">
              <p><strong>Origin of Raw Material:</strong> West Africa</p>
            </v-col>
            <v-col cols="12">
              <v-img src="./assets/world_en.png" alt="Powder &amp; Butter Cocoa" width="100%" />
            </v-col>
          </v-row>
        </section>
        <section id="ProductionProcedure">
          <h3 class="d-none">PRODUCTIONPROCEDURE</h3>
          <v-row>
            <v-col cols="12">
              <v-img class="mx-auto" contain src="./assets/Facilities2.png" alt="Facilities" width="664" height="215" />
            </v-col>

            <v-col cols="12">
              <v-img src="./assets/ProductionProcedure.png" alt="Powder &amp; Butter Cocoa" width="100%" />
            </v-col>
          </v-row>
        </section>
      </v-sheet>
    </v-main>
    <v-footer dark padless>
      <section id="contact">
        <h3 class="d-none">Contact</h3>
        <div id="contact-holder">
          <div class="row">
            <div class="large-8 large-centered columns page-spiel">
              <p class="text-white"></p>
            </div>
          </div>

          <div id="contact-form" class="row">
            <form action="#" method="post" class="peThemeContactForm">
              <div class="large-10 large-centered columns">
                <div class="form-upper">
                  <h5 class="text-white left">Name</h5>
                  <div class="input-holder">
                    <input id="form-name" name="author" data-fieldid="0" />
                  </div>
                </div>

                <div class="form-upper form-last">
                  <h5 class="text-white left">Email</h5>
                  <div class="input-holder">
                    <input id="form-email" name="email" data-fieldid="1" />
                  </div>
                </div>

                <div class="form-lower">
                  <h5 class="text-white left">Message</h5>
                  <div class="input-holder">
                    <input id="form-message" name="message" data-fieldid="2" />
                  </div>
                </div>

                <div id="form-button">
                  <h5><button type="submit">SEND</button></h5>
                </div>

                <div class="clearfix"></div>
                <br />

                <div id="contactFormSent" class="formSent response-message form-sent">
                  <i class="typcn typcn-thumbs-up"></i> Your message has been sent. Thank you!
                </div>
                <div id="contactFormError" class="formError response-message details-error">
                  <i class="typcn typcn-warning"></i> Please validate your fields.
                </div>
              </div>
            </form>
          </div>

          <div class="row">
            <div class="large-12 columns text-center">
              <div class="social-icons">
                <ul style="background-color:#000000"></ul>
                <div class="line"></div>
              </div>
            </div>
          </div>

          <div class="row">
            <div class="large-12 columns text-center">
              <h6 class="text-white copy-text">
                <!--<a href="http://www.monercocoa.com/aviso-legal">Disclaimer</a> · 
            <a href="http://www.monercocoa.com/politica-de-privacidad">Privacy Policy</a>-->
                © Copyright{{ new Date().getFullYear() }} cocoa.com
              </h6>
            </div>
          </div>
        </div>
        <!--end of contact-holder-->
      </section>
    </v-footer>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    // HelloWorld,
  },

  data() {
    return {
      drawer: false, // Hide mobile side menu by default
      navList: [
        {
          href: '#company',
          title: 'COMPANY',
        },
        {
          href: '#products',
          title: 'PRODUCTS',
        },
        {
          href: '#facilities',
          title: 'FACILITIES',
        },
        {
          href: '#ProductionProcedure',
          title: 'PRODUCTION PROCEDURE',
        },
      ],
      appBarBG: 'transparent',
      appBarMW: '1000px',
      carouselList: [
        {
          'background-image': require('./assets/CocoaBeans1.jpg'),
          src: require('./assets/MonerCocoa1.png'),
        },
        {
          'background-image': require('./assets/CocoaPowder.jpg'),
          src: require('./assets/MonerCocoa1.png'),
        },
        {
          'background-image': require('./assets/CocoaFruits.jpg'),
          src: require('./assets/MonerCocoa1.png'),
        },
      ],
      goToOptions: {
        duration: 1000,
      },
      productList: [
        {
          name: 'Natural Cocoa Butter',
          code: 'NCBT01',
          img: require('./assets/Powder-ButterCocoa1.png'),
          specificationList: [
            ['Color and Luster (Melting)', 'Light Golden Yellow'],
            ['Odor and Taste', 'Natural cocoa smell'],
          ],
        },
      ],
    };
  },
  methods: {
    onScroll() {
      // 'transparent'
      console.log(window);

      if (window.scrollY > window.innerHeight / 2) {
        this.appBarBG = 'black';
        this.appBarBG = null;
        this.appBarMW = null;
      } else {
        this.appBarBG = 'transparent';
        this.appBarMW = '1000px';
      }
    },
  },
};
</script>
<style lang="scss">
.yellow-showad {
  background-color: #e3dcc9 !important;
}
</style>
