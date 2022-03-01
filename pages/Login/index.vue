<template>
  <div class="form">
    <p>Login</p>
    <a-form-model ref="ruleForm" :rules="rules" :model="ruleForm">
      <a-form-model-item has-feedback prop="email">
        <a-input placeholder="Email" v-model="ruleForm.email" type="email">
          <a-icon
            slot="prefix"
            type="mail"
            style="color: rgba(0, 0, 0, 0.25)"
          />
        </a-input>
      </a-form-model-item>
      <a-form-model-item has-feedback prop="password">
        <a-input
          placeholder="Password"
          v-model="ruleForm.password"
          type="password"
        >
          <a-icon
            slot="prefix"
            type="lock"
            style="color: rgba(0, 0, 0, 0.25)"
          />
        </a-input>
      </a-form-model-item>
      <a-button type="primary" html-type="submit" @click="submitForm('ruleForm')">Login</a-button>
    </a-form-model>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    let validateEmail = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the email'))
      } else {
        if (this.ruleForm.email !== '') {
          let regex = new RegExp('[a-z0-9]+@[a-z]+\.[a-z]{2,3}')
          let result = regex.test(value)
          if (result) {
            callback()
          } else {
            callback(new Error('Please input the correct format email'))
          }
        }
        callback()
      }
    }

    let validatePass = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the password'))
      }else{
        if(this.ruleForm.pass !== ''){
          if(value.length < 6){
            callback(new Error('Password must at latest 6 character'))
          }
          this.$refs.ruleForm.validateField('pass')
        }
        callback()
      }
    }
    return {
      ruleForm: {
        email: '',
        password: '',
      },
      rules: {
        email: [{ validator: validateEmail, trigger: 'change' }],
        password: [{ validator: validatePass, trigger: 'change' }],
      },
    }
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert('submit')
          console.log(valid)
          
        } else {
          console.log('error submit')
          return false
        }
      })
    },
  },
}
</script>

<style>
.form {
  max-width: 450px;
  margin: 5% auto;
}
.form p {
  text-align: center;
  font-size: 30px;
  color: #000;
  font-weight: 500;
}
</style>
