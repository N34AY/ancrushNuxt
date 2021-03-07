<template>
  <form @submit.prevent="submit">
    <v-text-field
      v-model="name"
      label="Your name"
      :rules="validation.name"
      required
    ></v-text-field>
    <v-text-field v-model="email" label="Your email" required></v-text-field>
    <v-textarea
      v-model="other"
      label="Your message"
      no-resize
      rows="3"
      row-height="25"
      counter
      :rules="validation.other"
      required
    ></v-textarea>
    <v-radio-group v-model="type" mandatory row>
      <template v-slot:label>
        <div>Выберите тип <strong>заявки</strong></div>
      </template>
      <v-radio
        label="Заявка на вакансию"
        value="работа"
        color="blue"
      ></v-radio>
      <v-radio
        label="Заявка на анкету"
        value="анкета"
        color="success"
      ></v-radio>
    </v-radio-group>
    <v-btn rounded large @click="send" color="#AA00FF" class="white--text">
      Оставить заявку
    </v-btn>
  </form>
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
      validation: {
        name: [(v) => v.length <= 30 || 'Имя слишком длинное'],
        email: [(v) => v.length <= 40 || 'Почта слишком длинная'],
        other: [(v) => v.length <= 150 || 'Max 150 characters'],
      },
      name: '',
      email: '',
      other: '',
      type: '',
    }
  },

  methods: {
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
</style>