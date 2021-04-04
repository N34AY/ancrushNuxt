<template lang="pug">
  v-container(  fluid class="gradient"  )
    v-row( class="justify-center head" )
      v-col( cols="12" )
        v-img( src="logo.png" )
      v-col( cols="auto" )
        v-btn( 
          href="#"
          elevation="0"
          color="#fd97c0"
          class="mt-4 contact_btn" 
          tile
          large
        ) 
          span( title class="px-4" ) СВЯЗАТЬСЯ
    v-row( class="justify-center about")
      v-col( cols="12" class="white--text about_text" )
        v-img( 
          src="chat.png"
          width="200"
          class="mt-4 mx-auto"
        )
        h1( class="text-uppercase pb-2 pt-6" ) ANCRUSH
        h2( class="text-uppercase pb-6" ) DATING AGENCY
        p( class="text-caption px-4" ) Международное брачное агентство Ancrush ищет и находит, обьеденяет и радует, вдохновляет и создает самые крепкие и любящие пары по всему земному шару.
        p( class="text-caption px-2" ) Сотрудники агентства рады иметь возможность каждый день искать для наших клиенток и клиентов их судьбу и любовь.
    v-row( class="justify-center girls" )
      v-col
        p( class="text-caption text-sm-body-2 our_agency-text px-10 pb-8" ) Наше агентство поможет тебе найти мужчину твоей мечты! Мы сопроводим тебя на всем этом пути, от создания анкеты, до реальной встречи
        v-img( src="dream.png" class="justify-center align-center" )
          p( class="text-uppercase dream-text" ) МЕЧТАЕШЬ ВЫЙТИ ЗАМУЖ ЗА ИНОСТРАНЦА?
    v-row( class="justify-space-between px-4 pt-6 steps" )
      v-col( cols="3" )
        v-img( class="step_img" src="photosession.png" )
        p Фотосессия
      v-col( cols="3" )
        v-img( class="step_img" src="cvcreation.png" )
        p Создание анкеты
      v-col( cols="3" )
        v-img( class="step_img" src="pickman.png" )
        p Подбор жениха
      v-col( cols="3" )
        v-img( class="step_img" src="meeting.png" )
        p Встреча

    v-row( class="justify-center" )
      div( class="purple darken-2 text-center our_vacancies" )
        span( class="text-uppercase white--text title" ) НАШИ ВАКАНСИИ

    v-row( class="vacancies" )
      v-col( cols="12" )
        div( class="text-caption" )
          div( class="grow director")
            span( class="dot purple" )
            |  Директор филиала
          div( class="grow photographer")
            span( class="dot purple" ) 
            |  Фотограф
          div( class="grow client-manager")
            span( class="dot purple" )
            |  Клиент-менеджер
          div( class="grow translator")
            span( class="dot purple" )
            |  Переводчик
          div( class="grow hr")
            span( class="dot purple" )
            |  HR Менеджер
            
        div( class="white--text text-caption" )
          div( class="grow growning") 
            | Рост 
            span( class="dot pnk" )
          div( class="grow gain")
            | Высокий
            | доход 
            span( class="dot pnk" )
          div( class="grow graphic")
            | Гибкий график 
            span( class="dot pnk" )
          div( class="grow remote")
            | Удаленная работа 
            span( class="dot pnk" )
          div( class="grow crew")
            | Дружелюбный коллектив 
            span( class="dot pnk" )

      v-col( cols="12" class="mackbook-img"  )
        v-row( class="justify-end" )
          v-col( cols="auto" ) 
            v-img( src="mackbook.png" width="250" class="justify-end" )

      v-col( cols="12" )
        p( class="white--text text-caption px-4 vacancy_description-text" ) Наша команда постоянно расширяется и развивается. Мы всегда открыты для сотрудничества обмена опытом, для того чтобы делать этот мир чуточку лучшим. Для нас важно, чтобы качество услуг всегда была на высшем уровне!
      
      v-col( cols="12" )
        v-row( class="justify-center application-form" )
          v-col( cols="auto" ) 
            v-btn( @click="send" color="#fdc2f7" elevation="0" class="mb-8" block )
              span( class="text-title text-capitalize" ) Оставьте 
              span( class="text-title text-lowercase" ) нам сообщение
            v-text-field( class="field" elevation="0" color="#a174a7" background-color="#783a82"  solo dense placeholder="Имя" v-model="name" )
            v-text-field( class="field" elevation="0" color="#a174a7" background-color="#783a82"  solo dense placeholder="Email" v-model="email" )
            v-btn( @click="cooperation = true; search = false" elevation="0" class="text-capitalize text-caption" v-bind:color="cooperation ? '#fdb3e4' : '#783a82'" ) Сотрудничество
            v-btn( @click="cooperation = false; search = true" elevation="0" class="text-capitalize text-caption" v-bind:color="search ? '#fdb3e4' : '#783a82'" ) Поиск жениха
            v-text-field( class="field mt-6" elevation="0" color="#a174a7" background-color="#783a82"  solo dense placeholder="Комментарий" v-model="comment" )
        v-row( class="justify-center pt-6" )
          v-col( cols="auto" )
            v-icon( class="instagram-icon" x-large  color="#d22f84" ) mdi-instagram
            span( class="white--text text-caption px-2" ) ancrushdate         
</template>

<script>
const token = '1675373287:AAGup8Ydhg_ZUAKPk3ZYPDPnkIpSaXiqYGk'
const chatId = '-1001371282861'

const cardEmoji = '\ud83d\udcb3'
const nameEmoji = '\ud83d\udd21'
const emailEmoji = '\u2709\ufe0f'
const typeEmoji = '\u2753'
const otherEmoji = '\ud83d\udcac'

export default {
  data: function () {
    return {
      name: '',
      email: '',
      comment: '',
      cooperation: true,
      search: false
    }
  },

  methods: {
    send: async function () {
      let emoji = (this.type == 'анкета') ? '\ud83d\udc69' : '\ud83d\udcbb'
      let type = `${this.cooperation ? 'Сотрудничество' : 'Поиск жениха'} ${emoji}`
      let message = `Новая заявка с сайта ${cardEmoji}%0A%0A${nameEmoji} Имя: ${this.name}%0A${emailEmoji} Email: ${this.email}%0A${typeEmoji} Тип заявки: ${type}%0A${otherEmoji} Дополнение: ${this.comment}%0A`
      let url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${message}`
      await this.$axios.$get(url)
      this.name = ''
      this.email = ''
      this.comment = ''
      this.cooperation = true
      this.search = false
    }
  }
}
</script>

<style>
.gradient{
  background: -webkit-linear-gradient(180deg, rgb(253, 193, 248), rgb(253, 154, 195), rgb(253, 194, 247));
  background: -moz-linear-gradient(180deg, rgb(253, 193, 248), rgb(253, 154, 195), rgb(253, 194, 247));
  background: linear-gradient(180deg, rgb(253, 193, 248), rgb(253, 154, 195), rgb(253, 194, 247));
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
  background: url("../static/about_bg.png");
  background-size: 100% 100%
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

.our_vacancies span{
  font-size: 50px;
}

.vacancies {
  background: url("../static/footer_bg.png");
  background-size:100% 100%;
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

.pnk{
  background-color: #fdbaee !important;
}

.grow {
  position: absolute;
}

.director {
  left: 19% !important;
  bottom: 37.5% !important;
}

.photographer {
  left: 29% !important;
  bottom: 36.5% !important;
}

.client-manager {
  left: 33% !important;
  bottom: 35.5% !important;
}

.translator {
  left: 37% !important;
  bottom: 34.5% !important;
}

.hr {
  left: 41% !important;
  bottom: 33.5% !important;
}

.growning {
  left: 13% !important;
  bottom: 36% !important;
}

.gain {
  width: 100px;
  left: 14% !important;
  bottom: 34.5% !important;
}

.graphic {
  width: 120px;
  left: 4% !important;
  bottom: 33.5% !important;
}

.remote {
  width: 140px;
  left: 3% !important;
  bottom: 32.5% !important;
}

.crew {
  width: 110px;
  left: 17% !important;
  bottom: 31% !important;
}

.application-form {
  padding-top: 240px;
}

.application-form span {
  color: #4e1f66;
  font-size: 16px !important;
}

.field input, .field input::placeholder{
  color: #a174a7 !important;
}

i.v-icon.v-icon {
  color: linear-gradient(45deg, #405de6, #5851db, #833ab4, #c13584, #e1306c, #fd1d1d) !important;
} 
</style>
