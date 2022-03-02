<template>
  <div class="register">
    <h2>Register</h2>
    <a-form-model ref="form" :model="ruleForm" :rules="rules">
      <a-form-model-item has-feedback prop="username">
        <a-input placeholder="Username" v-model="ruleForm.username">
          <a-icon slot="prefix" type="user" />
        </a-input>
      </a-form-model-item>
      <a-form-model-item has-feedback prop="email">
        <a-input placeholder="Email" type="email" v-model="ruleForm.email">
          <a-icon slot="prefix" type="mail" />
        </a-input>
      </a-form-model-item>
      <a-form-model-item has-feedback prop="password">
        <a-input
          placeholder="Password"
          type="password"
          v-model="ruleForm.password"
        >
          <a-icon slot="prefix" type="lock" />
        </a-input>
      </a-form-model-item>
      <a-form-model-item has-feedback prop="confirmPass">
        <a-input
          placeholder="Confirm Password"
          type="password"
          v-model="ruleForm.confirmPass"
        >
          <a-icon slot="prefix" type="lock" />
        </a-input>
      </a-form-model-item>
      <a-form-model-item>
        <div class="header-register">
          <a-button
            type="primary"
            @click="submitForm('form')"
            html-type="submit"
          >
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
  data() {
    let validateUsername = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the username'))
      } else {
        if (value.length < 3) {
          callback(new Error('Username must be at least 3 charactrs long'))
        }
      }
      callback()
    }
    let validateEmail = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the email'))
      } else {
        let regex = new RegExp(/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/)
        let result = regex.test(value)
        if (result) {
          callback()
        } else {
          callback(new Error('Please input the correct format email'))
        }
      }
      callback()
    }
    let validatePassword = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the password'))
      } else {
        if (this.ruleForm.password !== '') {
          if (value.length < 6) {
            callback(new Error('Password must at latest 6 character'))
          }
          // this.$refs.form.validateField('password')
        }
        callback()
      }
    }
    let validateConfirmPassword = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the password again'))
      } else if (value != this.ruleForm.password) {
        callback(new Error("Two input don't match!"))
      } else {
        callback()
      }
    }
    return {
      ruleForm: {
        username: '',
        email: '',
        password: '',
        confirmPass: '',
      },
      rules: {
        username: [{ validator: validateUsername, trigger: 'change' }],
        email: [{ validator: validateEmail, trigger: 'change' }],
        password: [{ validator: validatePassword, trigger: 'change' }],
        confirmPass: [
          { validator: validateConfirmPassword, trigger: 'change' },
        ],
      },
    }
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          console.log({username: this.ruleForm.username,password: this.ruleForm.password,email: this.ruleForm.email});
        } else {
          console.log('err submit')
        }
      })
    },
  },
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
.header-register {
  display: flex;
  justify-content: space-between;
}
</style>
