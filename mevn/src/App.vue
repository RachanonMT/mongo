<template>
  <div class="sticky-top">
    <nav class="navbar navbar-dark bg-primary justify-content-between flex-nowrap flex-row">
      <div class="container">
        <router-link to="/" class="navbar-brand float-left">MEVN STACK</router-link>
        <ul class="nav navbar-nav flex-row float-right">
          <li class="nav-item">
            <router-link to="/" class="nav-link px-2">Create Student</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/view" class="nav-link px-2">View Student</router-link>
          </li>
        </ul>
      </div>
    </nav>
  </div>
  <div class="container">

    <router-view></router-view>
  </div>
</template>

<script>
export default {
}
</script>
