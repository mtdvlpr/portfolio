<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="8">
      <v-card id="about" class="mb-4">
        <v-card-title class="text-h4 justify-center"> About me </v-card-title>
        <v-card-text class="about">
          <v-img
            src="@/assets/img/me.webp"
            sizes="(max-width: 350px) 152px, (max-width: 700px) 192px, (max-width: 1300px) 384px, 512px"
            srcset="/me_152.webp 152w, /me_192.webp 192w, /me_384.webp 384w, /me_512.webp 512w"
            contain
            width="50%"
            max-width="512px"
            style="margin: 10px auto"
            alt="Picture of me"
          />
          <p>
            Hello, my name is Manoah. I am a web developer, currently a third
            year IT student at InHolland Haarlem. I enjoy programming, playing
            basketball and running.
          </p>
          <p>This purpose of this website is to show off my work and skills.</p>
          <p>
            As you can see, I am not a designer. My strength lies in the logic.
            I am very good at realizing the flow and logic of a component or
            page.
          </p>
          <p>
            Tools and technologies I have worked with include: Docker, MongoDB,
            MySQL, PHP, Express.js, Nuxt.js, React.js, SASS.
          </p>
        </v-card-text>
      </v-card>
      <v-card id="projects" class="mb-4">
        <v-card-title class="text-h4 justify-center"> Projects </v-card-title>
        <v-card-text>
          <projects-grid :cards="projects" :preview="true" />
        </v-card-text>
      </v-card>
      <v-card id="contact" class="mb-4">
        <v-card-title class="text-h4 justify-center"> Contact me </v-card-title>
        <v-card-text>
          <v-row>
            <v-col v-for="(link, i) in links" :key="i" cols="12" class="link">
              <v-icon left>{{ link.icon }}</v-icon>
              <a :href="link.to" :style="'color: ' + color">
                {{ link.title }}
              </a>
            </v-col>
            <v-col cols="12" class="link">
              <v-icon left>{{ mdiEmail }}</v-icon>
              <Mailto
                mail="149895ja@gmail.com"
                subject="Contact - manoahtervoort.tk"
                title="Send me an email"
                :style="'color: ' + color"
              >
                Send me an email
              </Mailto>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
import { mdiGithub, mdiLinkedin, mdiEmail } from '@mdi/js'
export default {
  data() {
    return {
      mdiEmail,
      projects: [
        {
          title: 'Mag Ik Dit Delen?',
          subtitle: 'MongoDB, Express, React, Node',
          image: 'midd.webp',
          to: 'https://magikditdelen.nl',
        },
        {
          title: 'Ai And You',
          subtitle: 'MySQL, PHP, JS, HTML5',
          image: 'aay.webp',
          to: 'http://aiandyou.csgja.com',
        },
      ],
      links: [
        {
          icon: mdiGithub,
          title: 'Discover my GitHub profile',
          to: 'https://github.com/mtdvlpr',
        },
        {
          icon: mdiLinkedin,
          title: 'Check me out on LinkedIn',
          to: 'https://www.linkedin.com/in/manoaht/',
        },
      ],
    }
  },
  head() {
    return {
      title: 'Home',
      link: [{ rel: 'canonical', href: 'https://www.manoahtervoort.tk' }],
    }
  },
  computed: {
    color() {
      return this.$vuetify.theme.dark ? 'white' : 'black'
    },
  },
}
</script>
<style lang="scss" scoped>
.v-card p {
  font-size: 1.5em;
}

@media screen and (max-width: 600px) {
  .about {
    min-height: 590px;
  }
}

@media screen and (max-width: 450px) {
  .about {
    min-height: 590px;
  }
}

@media screen and (max-width: 400px) {
  .about {
    min-height: 630px;
  }
}

@media screen and (max-width: 380px) {
  .about {
    min-height: 670px;
  }
}

@media screen and (max-width: 350px) {
  .about {
    min-height: 680px;
  }
}

@media screen and (max-width: 325px) {
  .about {
    min-height: 715px;
  }
}

@media screen and (max-width: 300px) {
  .about {
    min-height: 740px;
  }
}

.link {
  padding-left: 30%;

  a {
    font-size: 1.5em;
    text-decoration: none;

    &:hover {
      text-decoration: underline;
    }
  }
}

@media screen and (max-width: 1000px) {
  .link {
    padding-left: 10%;
  }
}
</style>
