<template lang="pug">
v-container.gradient(fluid)
  .head
    v-row.justify-center
      v-col(cols='auto')
        v-img(src='logo.png', max-width='700px')
    v-row.justify-center
      v-col(cols='auto')
        v-btn.mt-4.contact_btn(
          href='#',
          elevation='0',
          color='#fd97c0',
          tile,
          large
        ) 
          span.px-4(title) СВЯЗАТЬСЯ
  v-row.justify-center.align-center.about 
    v-col(xs='4', sm='6', lg='4', xl='4')
      v-img#phone.mt-4.mx-auto(
        src='chat.png',
        max-width='350',
        min-width='200'
      )
    v-col.white--text.about_text(xs='4', sm='6', lg='4', xl='4')
      h1.text-uppercase.pb-2.pt-6 ANCRUSH
      h2.text-uppercase.pb-6 DATING AGENCY
      p.text-caption.px-4 Международное брачное агентство Ancrush ищет и находит, обьеденяет и радует, вдохновляет и создает самые крепкие и любящие пары по всему земному шару.
      p.text-caption.px-2 Сотрудники агентства рады иметь возможность каждый день искать для наших клиенток и клиентов их судьбу и любовь.

  v-row.justify-center.girls.align-center
    v-col(xs='4', sm='6', lg='4', xl='4')
      p.text-caption.text-sm-body-2.our_agency-text.px-10.pb-8 Наше агентство поможет тебе найти мужчину твоей мечты! Мы сопроводим тебя на всем этом пути, от создания анкеты, до реальной встречи
    v-col(xs='4', sm='6', lg='4', xl='4')
      v-img.justify-center.align-center(src='dream.png', max-width='650')
        p.text-uppercase.dream-text МЕЧТАЕШЬ ВЫЙТИ ЗАМУЖ ЗА ИНОСТРАНЦА?

  v-row.justify-space-between.text-center.px-4.steps
    v-col.align-center(cols='3')
      v-img.mx-auto.step_img(src='photosession.png')
      p Фотосессия
    v-col(cols='3')
      v-img.mx-auto.step_img(src='cvcreation.png')
      p Создание анкеты
    v-col(cols='3')
      v-img.mx-auto.step_img(src='pickman.png')
      p Подбор жениха
    v-col(cols='3')
      v-img.mx-auto.step_img(src='meeting.png')
      p Встреча

  v-row.justify-center
    .purple.darken-2.text-center.our_vacancies
      span.text-uppercase.white--text.title НАШИ ВАКАНСИИ

  v-row
    v-col(xs='4', sm='6', lg='4', xl='4')
      .text-caption
        .grow.director
          span.dot.purple
          |
          | Директор филиала
        .grow.photographer
          span.dot.purple 
          |
          | Фотограф
        .grow.client-manager
          span.dot.purple
          |
          | Клиент-менеджер
        .grow.translator
          span.dot.purple
          |
          | Переводчик
        .grow.hr
          span.dot.purple
          |
          | HR Менеджер

      .white--text.text-caption
        .grow.growning 
          | Рост
          span.dot.pnk
        .grow.gain
          | Высокий
          | доход
          span.dot.pnk
        .grow.graphic
          | Гибкий график
          span.dot.pnk
        .grow.remote
          | Удаленная работа
          span.dot.pnk
        .grow.crew
          | Дружелюбный коллектив
          span.dot.pnk

  v-row.justify-center.vacancies
    v-col.mackbook-img(xs='12', sm='12', lg='12', xl='12')
      v-row.justify-end
        v-col(cols='auto') 
          v-img.justify-end(src='mackbook.png', width='250')

    v-col(xs='12', sm='12', lg='6', xl='6')
      p.white--text.text-caption.px-4.vacancy_description-text Наша команда постоянно расширяется и развивается. Мы всегда открыты для сотрудничества обмена опытом, для того чтобы делать этот мир чуточку лучшим. Для нас важно, чтобы качество услуг всегда была на высшем уровне!

    v-col(cols='12')
      v-row.justify-center.application-form
        v-col(cols='auto') 
          Application
      v-row.justify-center.pt-6
        v-col(cols='auto')
          v-icon.instagram-icon(x-large, color='#d22f84') mdi-instagram
          span.white--text.text-caption.px-2 ancrushdate
</template>

<script>
import Application from '~/components/Application'

const token = '1675373287:AAGup8Ydhg_ZUAKPk3ZYPDPnkIpSaXiqYGk'
const chatId = '-1001371282861'

const cardEmoji = '\ud83d\udcb3'
const nameEmoji = '\ud83d\udd21'
const emailEmoji = '\u2709\ufe0f'
const typeEmoji = '\u2753'
const otherEmoji = '\ud83d\udcac'

export default {
  components: {
    Application,
  },

  data: function () {
    return {
      name: '',
      email: '',
      comment: '',
      cooperation: true,
      search: false,
      valid: true,
      nameRules: [(v) => !!v || 'Имя обязательно'],
      emailRules: [
        (v) => !!v || 'E-mail обязателен',
        (v) =>
          /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(
            v
          ) || 'Некорректный E-mail',
      ],
    }
  },

  methods: {
    validate: async function () {
      let valid = this.$refs.form.validate()
      if (valid) await this.send()
    },
    send: async function () {
      let emoji = this.type == 'анкета' ? '\ud83d\udc69' : '\ud83d\udcbb'
      let type = `${
        this.cooperation ? 'Сотрудничество' : 'Поиск жениха'
      } ${emoji}`
      let message = `Новая заявка с сайта ${cardEmoji}%0A%0A${nameEmoji} Имя: ${this.name}%0A${emailEmoji} Email: ${this.email}%0A${typeEmoji} Тип заявки: ${type}%0A${otherEmoji} Дополнение: ${this.comment}%0A`
      let url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${message}`
      await this.$axios.$get(url)
      this.$refs.form.resetValidation()
      this.$refs.form.reset()
    },
  },
}
</script>

<style>
body::-webkit-scrollbar {
  width: 6px;
}

body::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
}

body::-webkit-scrollbar-thumb {
  background-color: #b729aa;
  outline: 1px solid slategrey;
}

.gradient {
  background: -webkit-linear-gradient(
    180deg,
    rgb(253, 193, 248),
    rgb(253, 154, 195),
    rgb(253, 194, 247)
  );
  background: -moz-linear-gradient(
    180deg,
    rgb(253, 193, 248),
    rgb(253, 154, 195),
    rgb(253, 194, 247)
  );
  background: linear-gradient(
    180deg,
    rgb(253, 193, 248),
    rgb(253, 154, 195),
    rgb(253, 194, 247)
  );
}

.head {
  padding-top: 120px;
  padding-bottom: 160px;
}

.contact_btn {
  color: #412163 !important;
}

.contact_btn span {
  font-size: 20px !important;
}

.about {
  /* height: 620px; */
  background: url('../static/about_bg.png');
  background-size: 100% 100%;
}

.about_text {
  text-align: center;
  margin-bottom: 120px;
  font-family: 'PT Sans' !important;
}

.about_text h1 {
  font-size: 20px;
  letter-spacing: 6px;
}

.about_text h2 {
  font-size: 16px;
  font-weight: 400;
  letter-spacing: 2px;
}

.about_text p {
  line-height: 1.3 !important;
  font-size: 16px !important;
  font-weight: 300 !important;
}

.girls {
  padding-top: 110px;
  padding-bottom: 30px;
  text-align: center;
}

.our_agency-text {
  color: #4e1f66;
  line-height: 1.3 !important;
}

.dream-text {
  color: #4e1f66;
  line-height: 1;
  letter-spacing: 3px;
  font-size: 14px;
  padding-top: 24px;
  padding-left: 85px;
  padding-right: 85px;
}

.steps {
  text-align: center;
  font-size: 12px;
}

.steps p {
  margin-top: 10px;
}

.step_img {
  width: 60px;
  height: 60px;
}

.our_vacancies {
  width: 200px;
  margin-top: 120px;
  margin-bottom: 80px;
}

.our_vacancies span {
  font-size: 50px;
}

.vacancies {
  background: url('../static/footer_bg.png');
  background-size: 100% 100%;
  padding-bottom: 180px;
}

.vacancy_description-text {
  text-align: center;
  line-height: 1.2 !important;
}

.mackbook-img {
  margin-top: 130px;
}

.dot {
  height: 8px;
  width: 8px;
  border-radius: 50%;
  display: inline-block;
}

.purple {
  background-color: #561e68 !important;
}

.pnk {
  background-color: #fdbaee !important;
}

.grow {
  position: absolute;
}

.director {
  left: 19% !important;
  bottom: 36% !important;
}

.photographer {
  left: 29% !important;
  bottom: 35% !important;
}

.client-manager {
  left: 33% !important;
  bottom: 34% !important;
}

.translator {
  left: 37% !important;
  bottom: 33% !important;
}

.hr {
  left: 41% !important;
  bottom: 32% !important;
}

.growning {
  left: 13% !important;
  bottom: 34.5% !important;
}

.gain {
  width: 100px;
  left: 14% !important;
  bottom: 33.5% !important;
}

.graphic {
  width: 120px;
  left: 4% !important;
  bottom: 32.5% !important;
}

.remote {
  width: 140px;
  left: 3% !important;
  bottom: 31.5% !important;
}

.crew {
  width: 110px;
  left: 17% !important;
  bottom: 30% !important;
}

@media (max-width: 320px) {
  .grow {
    display: none;
  }
}
@media (min-width: 375px) and (max-width: 420px) {
  .director {
    left: 19% !important;
    bottom: 36% !important;
  }

  .photographer {
    left: 29% !important;
    bottom: 35% !important;
  }

  .client-manager {
    left: 33% !important;
    bottom: 34% !important;
  }

  .translator {
    left: 37% !important;
    bottom: 33% !important;
  }

  .hr {
    left: 41% !important;
    bottom: 32% !important;
  }

  .growning {
    left: 13% !important;
    bottom: 34% !important;
  }

  .gain {
    width: 100px;
    left: 13% !important;
    bottom: 32.5% !important;
  }

  .graphic {
    width: 120px;
    left: 9% !important;
    bottom: 31.5% !important;
  }

  .remote {
    width: 140px;
    left: 7% !important;
    bottom: 30.5% !important;
  }

  .crew {
    width: 110px;
    left: 20% !important;
    bottom: 29% !important;
  }
}

@media (min-width: 420px) and (max-width: 500px) {
  .director {
    left: 19% !important;
    bottom: 35% !important;
  }

  .photographer {
    left: 29% !important;
    bottom: 34% !important;
  }

  .client-manager {
    left: 33% !important;
    bottom: 33% !important;
  }

  .translator {
    left: 37% !important;
    bottom: 32% !important;
  }

  .hr {
    left: 41% !important;
    bottom: 31% !important;
  }

  .growning {
    left: 15% !important;
    bottom: 33% !important;
  }

  .gain {
    width: 200px;
    left: 5% !important;
    bottom: 32% !important;
  }

  .graphic {
    width: 120px;
    left: 10% !important;
    bottom: 31% !important;
  }

  .remote {
    width: 140px;
    left: 8% !important;
    bottom: 30% !important;
  }

  .crew {
    width: 200px;
    left: 1% !important;
    bottom: 29% !important;
  }
}

@media (min-width: 500px) and (max-width: 544px) {
  .director {
    left: 19% !important;
    bottom: 34% !important;
  }

  .photographer {
    left: 29% !important;
    bottom: 33% !important;
  }

  .client-manager {
    left: 33% !important;
    bottom: 32% !important;
  }

  .translator {
    left: 37% !important;
    bottom: 31% !important;
  }

  .hr {
    left: 41% !important;
    bottom: 30% !important;
  }

  .growning {
    left: 15% !important;
    bottom: 32% !important;
  }

  .gain {
    width: 200px;
    left: 5% !important;
    bottom: 31% !important;
  }

  .graphic {
    width: 120px;
    left: 10% !important;
    bottom: 30% !important;
  }

  .remote {
    width: 140px;
    left: 8% !important;
    bottom: 29% !important;
  }

  .crew {
    width: 200px;
    left: 1% !important;
    bottom: 28% !important;
  }
}

@media (min-width: 500px) and (max-width: 544px) {
  .director {
    left: 19% !important;
    bottom: 34% !important;
  }

  .photographer {
    left: 29% !important;
    bottom: 33% !important;
  }

  .client-manager {
    left: 33% !important;
    bottom: 32% !important;
  }

  .translator {
    left: 37% !important;
    bottom: 31% !important;
  }

  .hr {
    left: 41% !important;
    bottom: 30% !important;
  }

  .growning {
    left: 15% !important;
    bottom: 32% !important;
  }

  .gain {
    width: 200px;
    left: 5% !important;
    bottom: 31% !important;
  }

  .graphic {
    width: 120px;
    left: 10% !important;
    bottom: 30% !important;
  }

  .remote {
    width: 140px;
    left: 8% !important;
    bottom: 29% !important;
  }

  .crew {
    width: 200px;
    left: 1% !important;
    bottom: 28% !important;
  }
}

@media (min-width: 1366px) {
  .director {
    left: 19% !important;
    bottom: 37% !important;
  }

  .photographer {
    left: 29% !important;
    bottom: 36% !important;
  }

  .client-manager {
    left: 33% !important;
    bottom: 35% !important;
  }

  .translator {
    left: 37% !important;
    bottom: 34% !important;
  }

  .hr {
    left: 41% !important;
    bottom: 33% !important;
  }

  .growning {
    left: 17% !important;
    bottom: 35% !important;
  }

  .gain {
    width: 200px;
    left: 18% !important;
    bottom: 34% !important;
  }

  .graphic {
    width: 120px;
    left: 24% !important;
    bottom: 33% !important;
  }

  .remote {
    width: 140px;
    left: 27% !important;
    bottom: 32% !important;
  }

  .crew {
    width: 200px;
    left: 28% !important;
    bottom: 31% !important;
  }
}

@media (min-width: 1900px) {
  .director {
    left: 25% !important;
    bottom: 35% !important;
  }

  .photographer {
    left: 29% !important;
    bottom: 34% !important;
  }

  .client-manager {
    left: 33% !important;
    bottom: 33% !important;
  }

  .translator {
    left: 37% !important;
    bottom: 32% !important;
  }

  .hr {
    left: 41% !important;
    bottom: 31% !important;
  }

  .growning {
    left: 22% !important;
    bottom: 33% !important;
  }

  .gain {
    width: 200px;
    left: 24% !important;
    bottom: 32% !important;
  }

  .graphic {
    width: 120px;
    left: 28% !important;
    bottom: 31% !important;
  }

  .remote {
    width: 140px;
    left: 31% !important;
    bottom: 30% !important;
  }

  .crew {
    width: 200px;
    left: 33% !important;
    bottom: 29% !important;
  }
}

i.v-icon.v-icon {
  color: linear-gradient(
    45deg,
    #405de6,
    #5851db,
    #833ab4,
    #c13584,
    #e1306c,
    #fd1d1d
  ) !important;
}
</style>
