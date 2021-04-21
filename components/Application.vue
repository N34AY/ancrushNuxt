<template lang="pug">
v-form( v-model="valid" ref="form" lazy-validation )
  v-text-field( class="field" elevation="0" background-color="#783a82"  solo dense placeholder="Имя" v-model="name" :rules="nameRules" required )
  v-text-field( class="field" elevation="0" background-color="#783a82"  solo dense placeholder="Email" v-model="email" :rules="emailRules" required )
  v-btn( @click="cooperation = true; search = false" elevation="0" class="text-capitalize text-caption" v-bind:color="cooperation ? '#fdb3e4' : '#783a82'" ) Сотрудничество
  v-btn( @click="cooperation = false; search = true" elevation="0" class="text-capitalize text-caption" v-bind:color="search ? '#fdb3e4' : '#783a82'" ) Поиск жениха
  //- v-text-field( class="field mt-6" elevation="0" color="#a174a7" background-color="#783a82"  solo dense placeholder="Комментарий" v-model="comment" )
  v-textarea( class="field mt-6" elevation="0" background-color="#783a82" no-resize rows="2" solo dense placeholder="Комментарий" v-model="comment" )
  v-btn( @click="validate" color="#fdc2f7" elevation="0" class="mb-8" block :disabled="!valid" )
    span( class="text-title text-capitalize" ) Отправить
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
      search: false,
      valid: true,
      nameRules: [ v => !!v || 'Имя обязательно' ],
      emailRules: [
        v => !!v || 'E-mail обязателен',
        v => /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(v) || 'Некорректный E-mail',
      ],
    }
  },

  methods: {
    validate: async function () {
      let valid = this.$refs.form.validate()
      if (valid) await this.send()  
    },
    send: async function () {
      let emoji = (this.type == 'анкета') ? '\ud83d\udc69' : '\ud83d\udcbb'
      let type = `${this.cooperation ? 'Сотрудничество' : 'Поиск жениха'} ${emoji}`
      let message = `Новая заявка с сайта ${cardEmoji}%0A%0A${nameEmoji} Имя: ${this.name}%0A${emailEmoji} Email: ${this.email}%0A${typeEmoji} Тип заявки: ${type}%0A${otherEmoji} Комментарий: ${this.comment}%0A`
      let url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${message}`
      await this.$axios.$get(url)
      this.$refs.form.resetValidation()
      this.$refs.form.reset()
    }
  }
}
</script>

<style>
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

.field textarea, .field textarea::placeholder{
  color: #a174a7 !important;
}
</style>