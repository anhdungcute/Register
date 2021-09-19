<template>
  <div id="register">
     
      <form class="register-form"  v-if="currentForm === 'register'"  @submit.prevent="submitRegister()">

        <div class="form-outline mb-4">
            <label >Your Name</label>
            <input type="text" v-model="userRe.name" class="form-control" />
            <span v-if="!$v.userRe.name.required && $v.userRe.name.$dirty" class="text-danger">Name is required!</span>
            <span v-if="!$v.userRe.name.alpha && $v.userRe.name.$dirty" class="text-danger">Name is required!</span>
        </div>

        <div class="form-outline mb-4">
            <label >Your Email</label>
            <input type="email" v-model="userRe.email" class="form-control" />
        <span
          v-if="(!$v.userRe.email.required || !$v.userRe.email.email) && $v.userRe.email.$dirty"
          class="text-danger"
        >Valid Email is required!</span>
        </div>

        <div class="form-outline mb-4">
            <label >Password</label>
           <input type="password" v-model="userRe.password" class="form-control" />
        <span
          v-if="!$v.userRe.password.required && $v.userRe.password.$dirty"
          class="text-danger"
        >Password is required!</span>
        <span
          v-if="!$v.userRe.password.minLength  && $v.userRe.password.$dirty"
          class="text-danger"
        >Password must be between {{ $v.userRe.password.$params.minLength.min}}  characters!</span>
        </div>


        <div class="form-check d-flex justify-content-center mb-5">
         <input type="checkbox" v-model="userRe.check" class="form-check-input me-2" />
        <label for="" class="form-check-label ">I agree all statements </label>
          <span v-if="!$v.userRe.check.required && $v.userRe.check.$dirty" class="text-danger">Check is required</span>
         
        </div>

        <div class="d-flex justify-content-center">
          <button type="submit" 
          class="btn btn-success btn-block btn-lg gradient-custom-4 text-body"
          >Register</button>
        </div>

        <p class="text-center text-muted mt-5 mb-0">Have already an account? 
          <a href="Login"  class="fw-bold text-body" 
           @click.prevent="toggleForm()"
           ><u>Login here</u></a>
        </p>

      </form>
      <form class="login-form" v-else>
        <div class="form-outline mb-4">
            <label class="form-label" for="form3Example3cg">Your Email</label>
          <input type="email"  
          class="form-control form-control-lg"
          v-model.trim="userLo.email"
            />
        
        </div>

        <div class="form-outline mb-4">
           <label class="form-label" for="form3Example4cg">Password</label>
          <input type="password"  
          class="form-control form-control-lg" 
          v-model.trim="userLo.password"
          
          />
         
        </div>


        <div class="form-check d-flex justify-content-center mb-5">
          <input
            class="form-check-input me-2"
            type="checkbox"
          />
          <label class="form-check-label" for="form2Example3g">
            I agree all statements in <a href="#!" class="text-body"><u>Terms of service</u></a>
          </label>
        </div>

        <div class="d-flex justify-content-center">
          <button type="submit" 
          class="btn btn-success btn-block btn-lg gradient-custom-4 text-body"
          @click.prevent="submitLogin()"
          >Login</button>
        </div>

        <p class="text-center text-muted mt-5 mb-0">Have already an account? <a href="#!"  
        class="fw-bold text-body"  
        @click.prevent="toggleForm()"
        ><u>Create an account</u></a>
        </p>

      </form>

  </div>
</template>

<script>
import { required,email,alpha,minLength } from 'vuelidate/lib/validators'
export default {
  data(){
    return{
      userRe:{
        name:'',
        email: '',
        password:'',
        comfim:'',
        check:''
      },
      
      userLo:{
        email:'',
        password:''
      },
       currentForm: 'register',
    }
  },
  validations:{
      userRe:{
        name: {required,alpha},
        email:{required,email},
        password:{required,minLength:minLength(6)},
        check:{required}
      }
  },
  methods: {
       toggleForm()
        {
            this.currentForm = this.currentForm === 'login' ? 'register' : 'login';
        },
        submitRegister(){
          this.$v.$touch();
            if (!this.$v.$invalid) {
                  alert('Register success ')
                }
        },
         submitLogin(){
          console.log(this.userLo)
        }

  },
 
}
</script>

<style>

</style>