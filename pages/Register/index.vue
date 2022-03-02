<template>
  <div class="register">
    <h2>Register</h2>
    <a-form-model ref="form" :model="ruleForm">
      <a-form-model-item>
        <a-input placeholder="Username" v-model="ruleForm.username">
          <a-icon slot="prefix" type="user"/>
        </a-input>
      </a-form-model-item>
      <a-form-model-item>
        <a-input placeholder="Email" type="email" v-model="ruleForm.email">
          <a-icon slot="prefix" type="mail" />
        </a-input>
      </a-form-model-item>
      <a-form-model-item>
        <a-input placeholder="Password" type="password" v-model="ruleForm.password">
          <a-icon slot="prefix" type="lock" />
        </a-input>
      </a-form-model-item>
      <a-form-model-item>
        <a-input placeholder="Confirm Password" type="password">
          <a-icon slot="prefix" type="lock" />
        </a-input>
      </a-form-model-item>
      <a-form-model-item>
        <div class="header-register">
          <a-button type="primary" @click="submitForm('form')" html-type="submit">
          Register
        </a-button>
        <nuxt-link to="/login">Already have an account</nuxt-link>
        </div>
      </a-form-model-item>
    </a-form-model>
  </div>
</template>

<script>
export default {
  name: 'Register',
  data(){
    return {
      ruleForm: {
        username: '',
        email: '',
        password: '',
      }
    }
  },
  methods: {
    submitForm(formName){
      this.$refs[formName].validate(valid=>{
        if(valid){
          console.log(valid);
        }else{
          console.log('err submit');
        }
      })
    }
  }
}
</script>

<style>
.register {
  max-width: 450px;
  margin: 5% auto;
}
.register h2 {
  text-align: center;
}
.header-register{
  display: flex;
  justify-content: space-between;
}
</style>
