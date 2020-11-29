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
      <v-carousel cycle height="100vh" hide-delimiter-background show-arrows-on-hover id="home">
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
      <div class="toTop">
        <span>
          <v-icon>home</v-icon>
        </span>
      </div>
      <div>
        <v-sheet class="mx-auto d-flex pt-10" color="#EBD0BB" width="901px">
          <v-sheet class="transparent">
            <v-sheet class="transparent d-flex align-center px-5" :width="outwidth">
              <v-sheet class="transparent flex-grow-1" height="896px">
                <v-sheet
                  class="transparent d-flex align-center justify-space-around"
                  style="margin-top:477px"
                  height="114px"
                >
                  <v-sheet
                    class="text-center d-flex justify-center align-center text-subtitle-1 font-weight-bold text-break"
                    width="114px"
                    height="100%"
                    rounded="circle"
                    elevation="3"
                    >{{ en.jinru }}</v-sheet
                  >
                  <v-icon style="transform:rotate(45deg)">mdi-arrow-top-right</v-icon>
                </v-sheet>
              </v-sheet>
              <v-sheet class="transparent">
                <v-sheet class="transparent text-center" width="220px" v-for="(value, index) of en.pre" :key="index">
                  <v-sheet
                    class="d-flex justify-center align-center"
                    width="100%"
                    height="40px"
                    rounded="pill"
                    elevation="3"
                  >
                    {{ value }}
                  </v-sheet>
                  <v-icon>mdi-chevron-down</v-icon>
                </v-sheet>
              </v-sheet>
            </v-sheet>
            <v-sheet class="transparent d-flex align-center" :width="outwidth">
              <v-sheet class="flex-grow-1 "></v-sheet>
              <v-sheet
                class="transparent d-flex align-end justify-center border-dashed px-5 "
                width="400px"
                height="400px"
              >
                <v-sheet
                  class="transparent text-center d-flex justify-center align-center text-h6 font-weight-bold text-break"
                  max-width="10em"
                  height="100%"
                  >{{ en.butter.name }}</v-sheet
                >
                <v-sheet class="transparent ">
                  <v-sheet
                    class="transparent text-center "
                    width="220px"
                    v-for="(value, index) of en.butter.list"
                    :key="index"
                  >
                    <v-sheet
                      class="d-flex justify-center align-center brown--text"
                      width="100%"
                      color="#ffe4e1"
                      height="40px"
                      rounded="pill"
                      elevation="3"
                    >
                      {{ value }}
                    </v-sheet>
                    <v-icon>mdi-chevron-down</v-icon>
                  </v-sheet>
                </v-sheet>
              </v-sheet>
            </v-sheet>
            <v-sheet class="d-flex transparent px-5 py-4" :width="outwidth">
              <v-spacer></v-spacer>
              <v-sheet class="transparent d-flex align-center justify-center" width="220px">
                <v-sheet
                  class="d-flex align-center justify-center text-subtitle-1 font-weight-bold "
                  rounded="pill"
                  width="140px"
                  height="60px"
                  elevation="3"
                  >{{ en.customer }}</v-sheet
                >
              </v-sheet>
            </v-sheet>
          </v-sheet>
          <v-sheet class="transparent">
            <v-sheet class="transparent d-flex align-center ">
              <v-sheet class="transparent flex-grow-1">
                <v-sheet
                  class="transparent d-flex align-center justify-space-around"
                  style="margin-top:-37px"
                  width="180px"
                  height="114px"
                >
                  <v-icon style="transform:rotate(-135deg)">mdi-arrow-top-right</v-icon>

                  <v-sheet
                    class="text-center d-flex justify-center align-center text-subtitle-1 font-weight-bold text-break"
                    width="114px"
                    height="100%"
                    rounded="circle"
                    elevation="3"
                    >{{ en.jinru }}</v-sheet
                  >
                </v-sheet>
              </v-sheet>
            </v-sheet>
            <v-sheet class="d-flex transparent px-5 py-4" style="margin-top:380px" :width="outwidth">
              <v-sheet class="transparent" width="50px"></v-sheet>

              <v-sheet class="transparent d-flex align-center justify-center" width="220px">
                <v-sheet
                  class="d-flex align-center justify-center text-subtitle-1 font-weight-bold "
                  rounded="pill"
                  width="140px"
                  height="60px"
                  elevation="3"
                >
                  {{ en.customer }}
                </v-sheet>
              </v-sheet>
            </v-sheet>
            <v-sheet class="transparent d-flex align-end" :width="outwidth">
              <v-sheet class="transparent flex-grow-1 d-flex align-center justify-center" style="margin-bottom:20px">
                <v-icon style="transform:rotate(45deg)">mdi-arrow-top-right</v-icon>
              </v-sheet>
              <v-sheet
                class="transparent d-flex align-start justify-center border-dashed px-5 "
                width="400px"
                :height="en.liquor.list.length * 64 + 16 + 'px'"
              >
                <v-sheet class="transparent ">
                  <v-sheet
                    class="transparent text-center "
                    width="220px"
                    v-for="(value, index) of en.liquor.list"
                    :key="index"
                  >
                    <v-icon>mdi-chevron-up</v-icon>

                    <v-sheet
                      class="d-flex justify-center align-center brown--text"
                      width="100%"
                      height="40px"
                      color="#ffe4e1"
                      rounded="pill"
                      elevation="3"
                    >
                      {{ value }}
                    </v-sheet>
                  </v-sheet>
                </v-sheet>
                <v-sheet
                  class="transparent text-center d-flex justify-center align-center text-h6 font-weight-bold text-break"
                  max-width="10em"
                  height="100%"
                >
                  {{ en.liquor.name }}
                </v-sheet>
              </v-sheet>
            </v-sheet>
            <v-sheet class="transparent d-flex align-start" :width="outwidth">
              <v-sheet class="transparent flex-grow-1 d-flex align-center justify-center" style="margin-top:20px">
                <v-icon style="transform:rotate(45deg)">mdi-arrow-top-right</v-icon>
              </v-sheet>
              <v-sheet
                class="transparent d-flex align-end justify-center border-dashed px-5 "
                width="400px"
                :height="en.powder.list.length * 64 + 12 + 'px'"
              >
                <v-sheet class="transparent ">
                  <v-sheet
                    class="transparent text-center "
                    width="220px"
                    v-for="(value, index) of en.powder.list"
                    :key="index"
                  >
                    <v-sheet
                      class="d-flex justify-center align-center  brown--text"
                      width="100%"
                      height="40px"
                      color="#c59887"
                      rounded="pill"
                      elevation="3"
                    >
                      {{ value }}
                    </v-sheet>
                    <v-icon>mdi-chevron-down</v-icon>
                  </v-sheet>
                </v-sheet>
                <v-sheet
                  class="transparent text-center d-flex justify-center align-center text-h6 font-weight-bold text-break"
                  max-width="10em"
                  height="100%"
                >
                  {{ en.powder.name }}
                </v-sheet>
              </v-sheet>
            </v-sheet>
            <v-sheet class="d-flex transparent px-5 py-4" :width="outwidth">
              <v-sheet class="transparent" width="50px"></v-sheet>

              <v-sheet class="transparent d-flex align-center justify-center" width="220px">
                <v-sheet
                  class="d-flex align-center justify-center text-subtitle-1 font-weight-bold "
                  rounded="pill"
                  width="140px"
                  height="60px"
                  elevation="3"
                >
                  {{ en.customer }}
                </v-sheet>
              </v-sheet>
            </v-sheet>
          </v-sheet>
        </v-sheet>
      </div>
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
          href: '#home',
          title: 'HOME',
        },
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
      en1: {
        jinru: '关键控制点',
        customer: '客户',
        pre: [
          '原料（可可豆）检测',
          '原料验检',
          '存储',
          '投料',
          '清杂',
          '去石',
          '焙炒',
          '仁壳分离',
          '灭菌/碱化',
          '粗磨',
          '精磨',
          '浆料存储',
          '均质',
          '压榨',
        ],
        liquor: {
          name: '可可液块加工子流程',
          list: ['运输','存储入库', '可可液块罐装/打包',  '调温',],
        },
        powder: {
          name: '可可粉加工子流程',
          list: ['磨粉', '冷却', '可可粉装袋', '存储入库', '运输'],
        },
        butter: {
          name: '可可脂加工子流程',
          list: ['毛油存储', '压滤', '压冷', '可可脂罐装/打包', '储存入库', '运输'],
        },
      },

      en: {
        jinru: 'CRITICAL CONTROL POINT',
        customer: 'CUSTOMER',
        pre: [
          'PRE-INSPECTION TEST',
          'COCOA BEAN RECEIPT',
          'WAREHOUSE/STORAGE',
          'COCOA BEANS TIPPING',
          'COCOA BEANS CLEANING',
          'COCOA BEAN DE-STONING',
          'COCOA BEANS ROASTING',
          'COCOA BEANS BREAKING',
          'STERILIZING/ALKALIZING',
          'COCOA BEAN WINNOWING',
          'COCOA NIB GRINDING',
          'LIQUOR STORAGE',
          'LIQUOR HOMOGENIZING',
          'LIQUOR PRESSING',
        ],
        liquor: {
          name: 'COCOA LIQUOR PROCESSING',
          list: ['LOADING & TRANSPORT', 'WAREHOUSE STORAGE', 'COCOA LIQUOR BAGGING', 'LIQUOR CONDITIONING'],
        },
        powder: {
          name: 'COCOA POWDER PROCESSING',
          list: [
            'CAKE PULVERIZING',
            'POWDER COOLING',
            'COCOA POWDER BAGGING',
            'WHAREHOUSE STORAGE',
            'LOADING & TRANSPORT',
          ],
        },
        butter: {
          name: 'COCOA BUTTER PROCESSING',
          list: [
            'DIRTY BUTTER TANK',
            'FILTERING',
            'TEMPERING',
            'BUTTER FILL/PACKING',
            'WHAREHOUSE STORAGE',
            'LOADING & TRANSPORT',
          ],
        },
      },
      outwidth: '450px',
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
body {
  font-size: 14px;
  .v-application {
    .border-dashed {
      border: 1px dashed #555 !important;
      border-radius: 20px !important;
    }
  }
}
.yellow-showad {
  background-color: #e3dcc9 !important;
}
.brown--text {
  color: #704214;
}
.toTop {
  position: fixed;
  bottom: 20px;
  right: 20px;
}
.fs-12 {
  font-size: 12px;
}
.fs-16 {
  font-size: 16px;
}
</style>
