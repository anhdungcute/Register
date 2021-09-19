<template>
  <div id="app">
    <section class="Re-Lo">
  <div class="mask d-flex align-items-center h-100 gradient-custom-3">
    <div class="container h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-12 col-md-9 col-lg-7 col-xl-6">
          <div class="card" style="border-radius: 15px;">
            <div class="card-body p-5">
              <h2 class="text-uppercase text-center mb-5">Create an account</h2>
                  <Register/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
  </div>
</template>

<script>
import Register from './components/Register.vue'


export default {
  components: { Register, },
  name: 'App',

}
</script>

<style >
  body{
    background-image: url(./assets/img4.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%;
  }
</style>
