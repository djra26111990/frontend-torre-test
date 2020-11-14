<template>
  <b-navbar toggleable="lg" type="dark" variant="dark">
    <b-navbar-brand href="./">TORRE</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      
      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
       <b-nav-item href="#">Search</b-nav-item>
       <b-nav-item href="#">Jobs</b-nav-item>
       <b-nav-item href="#">Your Genome</b-nav-item>
        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Your Profile</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>