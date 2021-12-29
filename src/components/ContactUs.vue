<template>
  <div class="container">
    <hr>
    <h3 class="subtitle is-3">Contact Us:</h3>
  <form ref="form" @submit.prevent="sendEmail" id="contactUs">
    
    <b-field>
      <b-input 
      placeholder="Name"
      type="text"
      name="user_name"
      required></b-input>
    </b-field>

    <b-field>
      <b-input 
      placeholder="Email"
      type="email"
      name="user_email"
      required></b-input>
    </b-field>

    <b-field>
      <b-input 
      placeholder="Message"
      type="textarea"
      minlength="50"
      maxlength="5000"
      name="message"
      required>
      </b-input>
    </b-field>

    <b-field>
      <b-input
      type="submit"
      value="Send"
      size="is-medium">
      </b-input>
    </b-field>

  </form>
  </div>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  methods: {
    sendEmail() {
      emailjs.sendForm('carmigo_test', 'contact_form', this.$refs.form, 'user_XVbIe1wrAqv1iZNKmMgfB')
        .then((result) => {
            alert('Email sent!', result.text)
            this.resetInputs()
        }, (error) => {
            alert('Error', error.text);
        });
    },
    resetInputs(){
      this.$refs["form"].reset();
  }
}
}
</script>

<style>

#contactUs {
  display: flex;
  flex-direction: column;
}

</style>