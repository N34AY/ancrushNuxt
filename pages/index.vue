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
        p( class="grow director")
          <span class="dot purple"></span> Директор филиала
      v-col( cols="12" )
        v-row( class="justify-end" )
          v-col( cols="auto" ) 
            v-img( src="mackbook.png" width="250" class="justify-end" )
      v-col( cols="12" )
        p( class="white--text text-caption px-4 vacancy_description-text" ) Наша команда постоянно расширяется и развивается. Мы всегда открыты для сотрудничества обмена опытом, для того чтобы делать этот мир чуточку лучшим. Для нас важно, чтобы качество услуг всегда была на высшем уровне!
      v-col( cols="12" )
        v-row( class="justify-center application-form" )
          v-col( cols="auto" ) 
            v-btn( color="#fdc2f7" )
              span( class="text-caption" ) Оставьте нам сообщение
            v-text-field( class="field" outlined dense placeholder="Ваше имя")
                
</template>
<script>
export default {}
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
  padding-bottom: 300px;
}

.vacancy_description-text {
  text-align: center;
  line-height: 1.2 !important;
}

.dot {
  height: 15px;
  width: 15px;
  border-radius: 50%;
  display: inline-block;
}

.dot .purple {
  background-color: #561e68;
}

.dot .pnk{
  background-color: #fdbaee;
}

.grow {
  position: absolute;
}

.grow .director {
  left: 17%;
  bottom: 22%;
}

.application-form {
  padding-top: 140px;
}

.field {
  background-color: #fdc2f7;
}
</style>
