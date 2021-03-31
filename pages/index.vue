<template lang="pug">
  v-container(  fluid class="gradient"  )
    v-row( class="justify-center head" )
      v-col( cols="auto" )
        v-img( src="logo.png")
      v-col( cols="auto" )
        v-btn( 
          href="#"
          elevation="0"
          color="#fd97c0"
          class="contact_btn" 
          class="mt-4" 
          tile
          large
        ) СВЯЗАТЬСЯ
    v-row( class="justify-center about")
      v-col( cols="12" class="white--text about_text" )
        v-img( 
          src="chat.png"
          width="200"
          class="mt-4 mx-auto"
        )
        h1( class="text-uppercase text-h6 pb-2" ) ANCRUSH
        h2( class="text-uppercase text-subtitle-2 pb-4" ) DATING AGENCY
        p( class="text-caption px-6" ) Международное брачное агентство Ancrush ищет и находит, обьеденяет и радует, вдохновляет и создает самые крепкие и любящие пары по всему земному шару.
        p( class="text-caption px-6" ) Сотрудники агентства рады иметь возможность каждый день искать для наших клиенток и клиентов их судьбу и любовь.
    v-row( class="justify-center girls" )
      v-col
        p( class="text-caption px-14 pb-8" ) Наше агентство поможет тебе найти мужчину твоей мечты! Мы сопроводим тебя на всем этом пути, от создания анкеты, до реальной встречи
        v-img( src="dream.png" class="justify-center align-center" )
          p( class="text-uppercase dream_text" ) МЕЧТАЕШЬ ВЫЙТИ ЗАМУЖ ЗА ИНОСТРАНЦА?
    v-row( class="justify-space-between px-4 pt-10 steps" )
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
      div( class="purple darken-2 text-center our_vacancies_text" )
        span( class="text-uppercase white--text text-h6" ) НАШИ ВАКАНСИИ
    v-row( class="vacancies" )
      v-col

        div( class="vacanices_bg" )
          p( class="grow director")
            <span class="dot purple"></span> Директор филиала
      
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

.about {
  height: 620px;
  background: url("../static/about_bg.png");
  background-size:100% 100%
}

.about_text {
  text-align: center;
}

.girls {
  padding-top: 100px;
  padding-bottom: 30px;
  text-align: center;
}

.dream_text {
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

.step_img {
  width: 60px;
  height: 60px;
}

.our_vacancies_text {
  width: 200px;
  margin-top: 140px;
  margin-bottom: 80px;
}

.vacancies {
  height: 620px;
  background: url("../static/vacancies_bg.png");
  background-size:100% 100%
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
</style>
