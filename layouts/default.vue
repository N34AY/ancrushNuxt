<template>
  <v-app dark>
    <v-app-bar color="transparent"
      absolute
      elevation="0"
    >
      <v-spacer />
      <v-btn text href="#about">О нас</v-btn>
      <v-btn text href="#vacancies">Вакансии</v-btn>
      <v-btn text href="#girls">Для девушек</v-btn>
      <v-btn text href="#contacts">Контакты</v-btn>
    </v-app-bar>
    <v-main>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      fixed: false,
      title: 'Ancrush'
    }
  }
}
</script>

<style>
.app__bar {
  background-color: transparent!important;
  border-color: transparent!important;
}

.container {
  margin: 0px;
  padding: 0px;
}
</style>
