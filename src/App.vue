<script>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>

    <div class="wrapper">
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
        
          <RouterLink class="navbar-brand" to="/">Navbar</RouterLink>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <RouterLink class="nav-link" to="/">Home <span class="sr-only">(current)</span></RouterLink>
              </li>
              <li class="nav-item">
                <RouterLink class="nav-link" to="/About">About Us</RouterLink>
              </li>
              <li class="nav-item">
                <RouterLink class="nav-link" to="/students">Students</RouterLink>
              </li>
              
              
            </ul>
            
          </div>
        </div>
       
      </nav>



    </div>
  </header>

  <RouterView />
</template>

<style scoped></style>
