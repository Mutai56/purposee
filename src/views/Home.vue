<i18n>
{
  "en": {
    "sections": {
        "1": {
          "title": "Purpose Centre",
          "subtitle": "Purpose Centre is a Christian based coaching organization, whose main objective is to support individual and organization development by nurturing a culture of psychological wellbeing for individuals, leaders, and institution development."
        },
        "about": {
          "title": "About Us",
          "subtitle": "Who we are and What are our goals",
          "row1": {
            "title": "Who we are, What we do, and What are our goals?",
            "content": "The Purpose Coaching Center was founded and registered in Kenya in 2019 by Lydiah Were. Our focus is on personal coaching and leadership training by nurturing a high culture of accountability. Purpose Coaching Centre assists young leaders in psychological wellness programs with further follow up on workplace principles on organizational development."
          },
          "row2": {
            "title": "Vision",
            "content": "To be a global leader for increased performance, self-actualization, achievement and well-being in individuals, teams, and organizations by utilizing evidence-based methods grounded in scientific research."
          },
          "row3": {
            "title": "Mission",
            "content": "Simplify mindful wellbeing for individuals with focus to productive contribution to their life, community and organizations."
          }
        },
        "gallery": {
          "title": "Gallery",
          "subtitle": "Take a look at our Portfolio",
          "book": "Book Now"
        },
        "videos": {
          "title": "Videos",
          "subtitle": "Take a look at one of our YouTube Videos"
        },
        "values": {
          "title": "Our Core Values",
          "subtitle": "Core Values of Purpose Coaching Centre",
          "founder": "About Our Founder"
        },
        "contact": {
          "subtitle": "Leave us a message and we'll reply as soon as possible"
        },
        "actions": {
          "contact": "Contact Us",
          "about": "More About Us",
          "values": "Our Core Values"
        }
    },
    "contact": {
      "subheader": "or contact us via:",
      "email": "Email Address",
      "facebook": "Facebook Page",
      "website": "Website",
      "phone": "Phone"
    },
    "map": {
      "title": "Our Location",
      "subtitle": "Feel Free To Pay Us A Visit"
    }
  }
}
</i18n>

<template>
  <div class="page page-sections">
    <section
      id="headerSection"
      data-section="home"
      class="header-section dark-gradient fullpage-section"
    >
      <animated-background />
      <v-container
        v-if="!loading"
        class="fill-height pt-12"
        :class="{ 'align-center': phoneOnly }"
      >
        <v-slide-y-transition appear>
          <h1 class="strong-text--text">
            <animate-text
              :duration="1500"
              :stop-after="0"
              :delay="500"
              :text="$t('sections.1.title')"
            />
          </h1>
        </v-slide-y-transition>
        <v-slide-x-transition appear>
          <h2 class="text--text mt-5">
            <animate-text
              @done="showSection1Actions = true"
              :duration="2500"
              :delay="2000"
              :text="$t('sections.1.subtitle')"
            ></animate-text>
          </h2>
        </v-slide-x-transition>
        <div
          class="actions"
          :class="{
            'fade-up-off': !showSection1Actions,
            'fade-up-on': showSection1Actions,
          }"
        >
          <v-btn
            @click="navigateToLink('#aboutSection')"
            color="strong-text"
            tile
            :large="pcOnly"
            depressed
            outlined
            class="me-6"
            >{{ $t("sections.actions.about") }}</v-btn
          >
          <v-btn
            @click="navigateToLink('#contactSection')"
            color="secondary"
            tile
            :large="pcOnly"
            outlined
            >{{ $t("sections.actions.contact") }}</v-btn
          >
        </div>
      </v-container>

      <div class="section-scroll-icon">
        <scroll-icon @click="scrollToSection(2)" />
      </div>
    </section>

    <e-section
      id="aboutSection"
      data-section="about"
      :headline="$t('sections.about.title')"
      :subtitle="$t('sections.about.subtitle')"
      light
      divider
    >
      <v-row class="flex-wrap justify-center pa-5 mb-5">
        <h1 class="headline">{{ $t("sections.about.row1.title") }}</h1>
        <p
          class="medium-text text-light--text mt-6 mt-lg-8"
          :class="{ 'text-center': phoneOnly }"
        >
          {{ $t("sections.about.row1.content") }}
        </p>
      </v-row>

      <v-row>
        <v-col
          :data-aos="pcOnly ? (isRtl ? 'fade-left' : 'fade-right') : 'fade-up'"
          data-aos-duration="800"
          :cols="pcOnly ? 5 : 12"
          class=""
        >
          <v-img
            src="/img/about-us.jpeg"
            contain
            width="100%"
            max-height="550"
          ></v-img>
        </v-col>
        <v-spacer></v-spacer>
        <v-col
          :data-aos="pcOnly ? (isRtl ? 'fade-right' : 'fade-left') : 'fade-up'"
          data-aos-duration="800"
          class="mt-6 mt-lg-0"
          :cols="pcOnly ? 6 : 12"
        >
          <h1 class="headline">{{ $t("sections.about.row2.title") }}</h1>
          <p
            class="medium-text text-light--text mt-6 mt-lg-8"
            :class="{ 'text-center': phoneOnly }"
          >
            {{ $t("sections.about.row2.content") }}
          </p>
          <h1 class="headline">{{ $t("sections.about.row3.title") }}</h1>
          <p
            class="medium-text text-light--text mt-6 mt-lg-8"
            :class="{ 'text-center': phoneOnly }"
          >
            {{ $t("sections.about.row3.content") }}
          </p>
          <div class="actions">
            <v-btn
              @click="navigateToLink('#valuesSection')"
              tile
              large
              depressed
              color="primary"
              >{{ $t("sections.values.title") }}</v-btn
            >
            <v-btn
              @click="goToFounderPage"
              tile
              large
              depressed
              color="secondary"
              class="float-right"
              >{{ $t("sections.values.founder") }}</v-btn
            >
          </div>
        </v-col>
      </v-row>
    </e-section>

    <e-section
      id="valuesSection"
      data-section="values"
      background="light"
      :headline="$t('sections.values.title')"
      :subtitle="$t('sections.values.subtitle')"
      light
    >
      <v-row class="flex-wrap justify-center">
        <v-col
          v-for="(value, i) in values"
          :key="i"
          :cols="pcOnly ? 6 : 12"
        >
          <v-card
            v-ripple="value.href ? { class: 'soft-ripple' } : false"
            data-aos="fade-up"
            :data-aos-duration="800"
            :data-aos-delay="400 * i"
            class="card-shadow fill-height text-center"
            :href="value.href ? value.href : ''"
            :target="value.href ? '_blank' : ''"
          >
            <div class="py-1 px-3">
              <v-card-title class="primary--text mb-1 justify-center">
                <div class="col-content">
                  <div
                    v-if="value.icon"
                    class="col-icon"
                  >
                    <v-icon :color="value.color + ' darken-1'" x-large>{{
                      value.icon
                    }}</v-icon>
                  </div>
                  <slot v-else :name="'icon' + i"></slot>

                  <br>
                  
                  <div>
                    <h3
                      v-if="value.title"
                      class="col-headline headline text--darken-2"
                      :class="`${value.color}--text`"
                    >
                      {{ value.title }}
                    </h3>
                    <slot v-else :name="'headline' + i"></slot>
                  </div>
                </div>
              </v-card-title>
              <v-card-subtitle>
                <v-list 
                  dense
                  v-for="item in value.subtitle" 
                  :key="item.id"
                  class="mb-n3"
                >
                  <v-list-item class="ml-n5 text-wrap">
                    <v-list-item-content>
                      {{ item.name }}
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-card-subtitle>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </e-section>

    <e-section
      id="gallerySection"
      data-section="gallery"
      :headline="$t('sections.gallery.title')"
      :subtitle="$t('sections.gallery.subtitle')"
      light
      divider
    >
      <v-row>
        <v-col
          :data-aos="pcOnly ? (isRtl ? 'fade-right' : 'fade-left') : 'fade-up'"
          data-aos-duration="800"
          cols="12"
        >
          <template>
            <v-carousel 
              cycle
            >
              <v-carousel-item
                v-for="(image, i) in images"
                :key="i"
                :src="image.src"
                reverse-transition="fade-transition"
                transition="fade-transition"
                hide-delimiter-background
                show-arrows-on-hover
              ></v-carousel-item>
            </v-carousel>
          </template>
        </v-col>
      </v-row>
    </e-section>

    <e-section
      id="videosSection"
      data-section="videos"
      :headline="$t('sections.videos.title')"
      :subtitle="$t('sections.videos.subtitle')"
      light
      divider
    >
      <v-row>
        <v-col
          :data-aos="pcOnly ? (isRtl ? 'fade-right' : 'fade-left') : 'fade-up'"
          data-aos-duration="800"
          cols="12"
        >
          <template>
            <YouTubeVideo />
          </template>
          <div class="actions d-flex mt-8 justify-center">
            <v-btn
              @click="navigateToLink('#contactSection')"
              tile
              large
              depressed
              color="secondary"
            >
              {{ $t("links.contact") }}
            </v-btn>
          </div>
        </v-col>
      </v-row>
    </e-section>

    <e-section
      id="contactSection"
      data-section="contact"
      :headline="$t('links.contact')"
      :subtitle="$t('sections.contact.subtitle')"
      light
    >
      <v-row class="justify-center px-lg-12">
        <v-col :cols="pcOnly ? 6 : 12" class="ps-lg-12">
          <contact-form data-once :data-aos="'fade'" :data-aos-duration="800" />
        </v-col>
        <v-col v-if="pcOnly" cols="1" class="text-center">
          <v-divider vertical></v-divider>
        </v-col>
        <v-col :cols="pcOnly ? 3 : 12">
          <div :data-aos="'fade'" :data-aos-duration="800">
            <v-subheader>
              {{ $t("contact.subheader") }}
            </v-subheader>
            <v-list two-line>
              <v-list-item
                v-for="item in contactItems"
                :key="item.name"
                :target="item.href ? '_blank' : ''"
                :href="item.href ? item.href : item.name === 'email' ? `mailto:${item.value}` : ''"
              >
                <v-list-item-icon>
                  <v-icon :color="item.color">{{ item.icon }}</v-icon>
                </v-list-item-icon>
                <v-list-item-content>
                  <v-list-item-subtitle class="mb-2">{{ $t("contact." + item.name) }}</v-list-item-subtitle>
                  <v-list-item-title class="text-wrap">{{ item.value }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </div>
        </v-col>
      </v-row>
    </e-section>

    <e-footer />

    <scroll-to-top />
  </div>
</template>

<script>
// @ is an alias to /src
import "particles.js";
import AOS from "aos";
import "aos/dist/aos.css"; // You can also use <link> for styles
import ScrollToTop from "@/components/custom/scroll-to-top";
import AnimateText from "@/components/custom/animate-text";
import ScrollIcon from "@/components/custom/scroll-icon";
import ContactForm from "@/components/custom/contact-form";
import AnimatedBackground from "@/components/custom/animated-background";
import ESection from "@/components/default/e-section";
import EFooter from "@/components/main/e-footer";
import GlobalComputed from "@/helpers/global-computed";
import GlobalMethods from "@/helpers/global-methods";
import YouTubeVideo from '../components/YouTubeVideo.vue';

export default {
  name: "Home",
  components: {
    ScrollToTop,
    ContactForm,
    AnimateText,
    ESection,
    ScrollIcon,
    EFooter,
    AnimatedBackground,
    YouTubeVideo
  },
  data() {
    return {
      showSection1Actions: false,
      currentScrollTop: 0,
      videoId: "",

      images: [
        {
          src: '/img/gallery/1.jpeg',
        },
        {
          src: '/img/gallery/2.jpeg',
        },
        {
          src: '/img/gallery/3.jpeg',
        },
        {
          src: '/img/gallery/4.jpeg',
        },
        {
          src: '/img/gallery/5.jpeg',
        },
        {
          src: '/img/gallery/6.jpeg',
        },
        {
          src: '/img/gallery/7.jpeg',
        },
        {
          src: '/img/gallery/8.jpeg',
        },
      ],

      contactItems: [
        {
    name: "whatsapp",
    icon: "mdi-whatsapp",
    value: "+254 796 614 853",
    color: "green darken-1",
    href: "https://wa.me/254796614853", // WhatsApp link
  },


        {
          name: "email",
          icon: "mdi-email",
          value: "info@purpose-centre.com",
          color: "secondary",
        },
        {
          name: "facebook",
          icon: "mdi-facebook",
          value: "@PurposeCentreKe",
          color: "blue darken-1",
          href: "",
        },
        {
          name: "phone",
          icon: "mdi-phone",
          value: "+254 796 614 853",
          color: "grey",
          href: "tel:+254796614853",
        },
      ],

      values: [
        {
          color: 'accent', 
          icon: 'mdi-monitor-cellphone-star',
          title: "Integrity", 
          subtitle: [
            {
              id: 1,
              name: "We communicate and deliver our programs with ethical standards of individual and group honesty.  We connect openly and credibly with each other and our clients.",
            },
          ]
        },
        {
          color: 'secondary', 
          icon: 'mdi-church-outline',
          title: "Faith",
          subtitle: [
            {
              id: 1,
              name: "We believe the Bible to be the only inspired, trustworthy Word of God. And we know that in all things God works for the good of those who love him, who have been called according to his purpose.",
            },
          ]
        },
        {
          color: 'primary', 
          icon: 'mdi-account-group',
          title: "Community Service",
          subtitle: [
            {
              id: 1,
              name: "We design and deliver with right skills and knowledge for our clients and assist them in seeking solutions to a range of personal, social and organizational issues.",
            },
          ]
        },
        {
          color: 'success', 
          icon: 'mdi-diversify',
          title: "Diversity",
          subtitle: [
            {
              id: 1,
              name: "We foster an environment of Equity, Inclusion and belonging to ensure we treat each other and our clients with respect and dignity.",
            },
          ]
        },
        {
          color: 'error', 
          icon: 'mdi-bookmark-outline',
          title: "Innovation",
          subtitle: [
            {
              id: 1,
              name: "We foster high standards of accountability in our engagement through collaboration, multidisciplinary resourcefulness, and self-activating thinking in everything we do.",
            },
          ]
        },
      ],
    };
  },
  computed: {
    ...GlobalComputed,
  },
  methods: {
    goToFounderPage() {
      this.$router.push('/our-founder')
    },

    scrollToSection(n) {
      let i = n - 1,
        element = document.querySelectorAll(".page-sections section")[i];
      if (element) {
        this.scrollToElement(element);
      }
    },

    openGoogleMap() {
      window.open("https://maps.google.com/maps?q=-1.2287111%2C36.9894515&amp;z=17&amp;hl=en", "_blank"); 
    },

    scrollObserver() {
      window.addEventListener("scroll", () => {
        this.currentScrollTop = document.documentElement.scrollTop;
      });
    },

    handleScrollChange(scrollTop) {
      const sections = document.querySelectorAll(".page-sections section");
      sections.forEach((section) => {
        let offsetTop = section.offsetTop - this.navbarHeight, // decrease navbarHeight
          offsetBottom = offsetTop + section.offsetHeight;

        if (scrollTop >= offsetTop && scrollTop < offsetBottom) {
          let sectionName = section.getAttribute("data-section");
          if (sectionName) {
            this.$store.commit("SET_ACTIVE_SECTION", sectionName);
          }
          // section is visible...
          if (section.getAttribute("data-theme") === "light") {
            if (!this.lightNavbar) {
              this.$store.dispatch("SET_LIGHT_NAVBAR", true);
            }
          } else {
            if (this.lightNavbar) {
              this.$store.dispatch("SET_LIGHT_NAVBAR", false);
            }
          }
        }
      });
    },
    
    ...GlobalMethods,
  },
  watch: {
    currentScrollTop(top) {
      this.handleScrollChange(top);
    },
  },

  mounted() {
    localStorage.clear();
    this.scrollObserver();
    AOS.init({
      container: document.documentElement,
      once: true,
      easing: "ease",
    });
  },
};
</script>

<style lang="scss" scoped>
section {
  .container {
    z-index: 1;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;

    &,
    * {
      z-index: 1;
    }
  }

  &.header-section {
    color: white;
  }

  h1 {
    font-size: 4rem;
    font-weight: 300;

    @media (max-width: 960px) {
      text-align: center;
      font-size: 1.7rem;
      line-height: 2.4rem;
      font-weight: 400;
    }
  }

  h2 {
    font-size: 1.78rem;
    word-break: break-word !important;
    font-weight: 200;

    @media (max-width: 960px) {
      text-align: center;
      font-size: 1.3rem;
      font-weight: 300;
    }
  }

  .actions {
    margin-top: 3rem;

    @media (max-width: 960px) {
      margin: 2rem 0;
      width: 100%;
      text-align: center;
      justify-content: center;
    }

    .v-btn {
      @media (min-width: 960px) {
        min-width: 130px;
        min-height: 45px;
      }
    }
  }

  .section-scroll-icon {
    z-index: 2;
    position: absolute;
    bottom: 8%;
    left: 50%;
    transform: translateX(-50%);
  }
}
</style>