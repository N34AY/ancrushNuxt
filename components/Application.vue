<template lang="pug">
  v-form( 
    class="form" 
    ref="form"
    v-model="valid"
    lazy-validation
  )
    v-text-field(
      label="Ваше имя"
      v-model="name"
      :rules="nameRules"
      required
    )
    v-text-field(
      label="Ваш Email" 
      v-model="email" 
      :rules="emailRules"
      required
    )
    v-textarea(
      label="Ваше сообщение"
      v-model="other"
      no-resize
      rows="3"
      row-height="25"
      counter
      required
    )
    v-radio-group( v-model="type" mandatory row )
      template( v-slot:label )
        div Выберите тип 
          strong заявки
      v-radio(
        label="Заявка на вакансию"
        value="работа"
        color="blue"
      )
      v-radio(
        label="Заявка на анкету"
        value="анкета"
        color="success"
      )
    v-btn( rounded large @click="validate" :disabled="!valid" color="#AA00FF" class="white--text" ) Оставить заявку
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
  name: 'Application',

  data: function () {
    return {
      valid: true,
      name: '',
      nameRules: [ v => !!v || 'Имя обязательно!' ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail обязателен!',
        v => /.+@.+\..+/.test(v) || 'Введите корректный E-mail',
      ],
      other: '',
      type: ''
    }
  },

  methods: {
    validate: async function () {
      let valid = this.$refs.form.validate()
      if (valid) this.send()
    },
    send: async function () {
      let emoji = (this.type == 'анкета') ? '\ud83d\udc69' : '\ud83d\udcbb'
      let type = `${this.type} ${emoji}`
      let message = `Новая заявка с сайта ${cardEmoji}%0A%0A${nameEmoji} Имя: ${this.name}%0A${emailEmoji} Email: ${this.email}%0A${typeEmoji} Тип заявки: ${type}%0A${otherEmoji} Дополнение: ${this.other}%0A`
      let url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${message}`
      await this.$axios.$get(url)
    },
  },
}
</script>

<style>
@media screen and (max-device-width: 1500px) {
  .form {max-width: 650px;}
}
</style>