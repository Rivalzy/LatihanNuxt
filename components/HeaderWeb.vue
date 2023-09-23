<template>
  <nav class="navbar navbar-expand-md navbar-light bg-light">
    <div class="container">
      <a class="navbar-brand" href="#">Taskist</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div id="navbarSupportedContent" class="collapse navbar-collapse">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/">Home</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/app">Todo</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/latihan">Latihan</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/lifecycle">Lifecycle</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/form">Form</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/list">List</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/articles">Articles</nuxt-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
