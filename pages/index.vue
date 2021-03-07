<template>
  <div>
    <section id="head">
      <v-container fluid class="video__container">
        <video src="../assets/video.webm" loop muted autoplay></video>
        <div class="video__content">
          <v-btn
            href="#"
            x-large
            color="red darken-1"
            class="white--text"
            depressed
            rounded
            >Связаться с нами</v-btn
          >
          <p>Очень крутой мотивирующий текст</p>
        </div>
      </v-container>
    </section>

    <section id="about">
      <v-container fluid>
        <v-row>
          <v-col cols="7" class="about__text">
            <h1 class="mb-10 text-h4">
              Dramatically re-engineer transparent deliverables with
              <span class="red--text text-h4">....</span>
            </h1>
            <p class="mb-4">
              Efficiently morph standards compliant quality vectors through
              high-quality interfaces. Credibly plagiarize low-risk high-yield
              methods of empowerment whereas frictionless opportunities.
              Globally plagiarize cross-platform content via standardized
              results.
            </p>
            <p>
              Continually seize bleeding-edge channels after sticky schemas.
              Monotonectally supply compelling collaboration and idea-sharing.
            </p>
          </v-col>
          <v-col cols="5">
            <div class="about__triangle"></div>
          </v-col>
        </v-row>
      </v-container>
    </section>

    <section id="girls">
      <v-container fluid>
        <v-img src="background.png" height="700">
          <h1 class="girls_text text-center text-h4">
            Continually evolve next-generation relationships
          </h1>
          <v-row class="girls_content text-center">
            <v-col cols="4">
              <img src="left_icon.png" alt="" />
              <h3>Continually utilize quality</h3>
              <p>
                Dynamically deliver functional paradigms whereas reliable
                strategic theme areas. Monotonectally fabricate competitive
                models via team.
              </p>
            </v-col>

            <v-col cols="4">
              <img src="center_icon.png" alt="" />
              <h3>Continually utilize quality</h3>
              <p>
                Dynamically deliver functional paradigms whereas reliable
                strategic theme areas. Monotonectally fabricate competitive
                models via team.
              </p>
            </v-col>

            <v-col cols="4">
              <img src="right_icon.png" alt="" />
              <h3>Continually utilize quality</h3>
              <p>
                Dynamically deliver functional paradigms whereas reliable
                strategic theme areas. Monotonectally fabricate competitive
                models via team.
              </p>
            </v-col>
          </v-row>
        </v-img>
      </v-container>
    </section>

    <section id="vacancies">
      <v-container fluid>
        <v-row>
          <v-col cols="5" class="vacancies__image">
            <div class="figure">
              <img src="macbook.png" alt="" />
            </div>
          </v-col>
          <v-col cols="7" class="vacancies__text">
            <h1 class="mb-10 text-h4">
              Dramatically re-engineer transparent deliverables with
              <span class="red--text text-h4">....</span>
            </h1>
            <p class="mb-4">
              Efficiently morph standards compliant quality vectors through
              high-quality interfaces. Credibly plagiarize low-risk high-yield
              methods of empowerment whereas frictionless opportunities.
              Globally plagiarize cross-platform content via standardized
              results.
            </p>
            <p>
              Continually seize bleeding-edge channels after sticky schemas.
              Monotonectally supply compelling collaboration and idea-sharing.
            </p>
          </v-col>
        </v-row>
      </v-container>
    </section>

    <section id="application">
      <v-container fluid>
        <Application />
      </v-container>
    </section>

    <section id="contacts">
      <v-container fluid>
        <v-row>
          <v-col
            cols="6"
            style="padding: 140px"
            class="white--text font-weight-bold"
          >
            <h1 class="mb-10 text-h2 text-uppercase">Get in touch</h1>
            <p>
              Continually seize bleeding-edge channels after sticky schemas.
              Monotonectally supply compelling collaboration and idea-sharing.
              Continually seize bleeding-edge channels after sticky schemas.
            </p>
            <p>
              Continually seize bleeding-edge channels after sticky schemas.
              Monotonectally supply compelling collaboration and idea-sharing.
            </p>
          </v-col>
          <v-col cols="6">
            <v-card elevation="2" class="contacts__card text-center">
              <v-card-text>
                <h1 class="mb-2 text-h6 text-uppercase">call us</h1>
                <p>+380682281488</p>
                <p>+380682281488</p>
                <h1 class="mt-4 mb-2 text-h6 text-uppercase">location</h1>
                <p>
                  Continually seize bleeding-edge channels after sticky schemas.
                  Monotonectally supply compelling collaboration and
                  idea-sharing.
                </p>
                <h1 class="mt-4 text-h6 text-uppercase">social networks</h1>
                <v-row class="mt-4">
                  <v-col>
                    <v-btn icon href="#">
                      <v-icon large color="#E1306C"> mdi-instagram </v-icon>
                    </v-btn>
                  </v-col>
                  <v-col>
                    <v-btn icon href="#">
                      <v-icon large color="#3b5998"> mdi-facebook </v-icon>
                    </v-btn>
                  </v-col>
                  <v-col>
                    <v-btn icon href="#">
                      <v-icon large color="#0088cc"> mdi-telegram </v-icon>
                    </v-btn>
                  </v-col>
                </v-row>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </section>
  </div>
</template>

<script>
import Application from '~/components/Application.vue'

export default {
  components: {
    Application,
  },

  data: function () {
    return {}
  },
}
</script>

<style>
.video__container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100%;
}

video {
  height: 100vh;
  width: 100%;
  object-fit: cover;
}

.video__content {
  text-align: center;
  position: absolute;
}

.about__triangle {
  position: absolute;
  right: 0;
  margin-bottom: 0;
  border-bottom: 700px solid #fb8686;
  border-left: 700px solid transparent;
}

.about__text {
  padding: 200px;
}

.girls_text {
  position: relative;
  top: 20%;
  margin-bottom: 40px;
}

.girls_content {
  position: relative;
  top: 30%;
  padding-left: 200px;
  padding-right: 200px;
}

.figure {
  width: 0;
  height: 700px;
  border-bottom: 700px solid #fb8686;
  border-right: 700px solid transparent;
}

.figure img {
  padding: 120px;
}

.vacancies__text {
  padding: 220px;
}

#application {
  background-color: #f6f5f3;
}

form {
  padding-top: 60px;
  max-width: 900px;
  padding-left: 140px;
  padding-bottom: 60px;
}

#contacts {
  background-color: #dfa5c6;
}

.contacts__card {
  transform: translateY(-50%);
  max-width: 400px;
  margin-left: 200px;
}

.contacts__card .row {
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 10px;
}
</style>