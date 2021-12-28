<template>
  <form ref="form" @submit.prevent="sendEmail" id="contactUs">
    <label>Name</label>
    <input type="text" name="user_name">
    <label>Email</label>
    <input type="email" name="user_email">
    <label>Message</label>
    <textarea name="message"></textarea>
    <input type="submit" value="Send">
  </form>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  methods: {
    sendEmail() {
      emailjs.sendForm('carmigo_test', 'contact_form', this.$refs.form, 'user_XVbIe1wrAqv1iZNKmMgfB')
        .then((result) => {
            console.log('SUCCESS!', result.text);
        }, (error) => {
            console.log('FAILED...', error.text);
        });
    }
  }
}
</script>

<style>

#contactUs {
  background-color: rgba(255,255,255,.6);
  text-align: center;
}

</style>