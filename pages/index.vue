<template>
  <div>
    <NavBar />

    <div class="container">
      <div class="card">
        <div class="card-header">
          <h1>Welcome to our Online Shoe Shop</h1>
        </div>
        <div class="card-body">
          <blockquote class="blockquote mb-0">
            <p>“You're off to Great Places! Today is your day! Your mountain is waiting, So... get on your way!”</p>
            <footer class="blockquote-footer"> Dr.  Seus</footer>
          </blockquote>
        </div>      
        <div class="card-body">
          <a class="btn btn-primary btn-lg btn-block" href="/register" role="button">Register</a>
          <a class="btn btn-primary btn-lg btn-block" href="/login" role="button">Login</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  auth: false
}
</script>
<style scoped>
.card{
  margin: 20px;
  margin-top: 50px;
}
h1{
  text-align: center;
}
</style>