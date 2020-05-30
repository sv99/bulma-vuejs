<template>
  <div id="app">
    <nav v-if="$route.name !== 'Login'" class="navbar has-shadow">
      <div class="navbar-brand">
        <a class="navbar-item" href="#">
          <img src="src/assets/logo.png" alt="Bleeding Edge Press" />
        </a>
        <div class="navbar-burger burger">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>

      <div class="navbar-menu">
        <div class="navbar-start">
          <div class="navbar-item">
            <small>Publishing at the speed of technology</small>
          </div>
        </div>

        <div class="navbar-end">
          <div class="navbar-item has-dropdown is-hoverable">
            <div class="navbar-link">
              John Doe
            </div>
            <div class="navbar-dropdown">
              <a class="navbar-item">
                <span class="icon is-small">
                  <i class="fa fa-user-circle-o"></i>
                </span>
                Profile
              </a>
              <a class="navbar-item" @click="openBugReport = true">
                <span class="icon is-small">
                  <i class="fa fa-bug"></i>
                </span>
                Report bug
              </a>
              <a class="navbar-item">
                <span class="icon is-small">
                  <i class="fa fa-sign-out"></i>
                </span>
                Sign Out
              </a>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <section v-if="$route.name !== 'Login'" class="section">
      <div class="columns">
        <div class="column is-4-tablet is-3-desktop is-2-widescreen">
          <aside class="menu">
            <p class="menu-label">Menu</p>
            <ul class="menu-list">
              <li>
                <router-link to="/dashboard">
                  <span class="icon">
                    <i class="fa fa-tachometer-alt"></i>
                  </span>
                  Dashboard
                </router-link>
              </li>
              <li>
                <router-link to="/books">
                  <span class="icon">
                    <i class="fa fa-book"></i>
                  </span>
                  Books
                </router-link>
              </li>
              <li>
                <router-link to="/customers">
                  <span class="icon">
                    <i class="fa fa-address-book"></i>
                  </span>
                  Customers
                </router-link>
              </li>
              <li>
                <router-link to="/orders">
                  <span class="icon">
                    <i class="fa fa-file-alt"></i>
                  </span>
                  Orders
                </router-link>
              </li>
            </ul>
          </aside>
        </div>
        <main class="column">
          <transition><router-view /></transition>
        </main>
      </div>
    </section>
    <div v-else>
      <router-view />
    </div>
    <transition>
      <bug-report
        :show-modal="openBugReport"
        @close="openBugReport = false"
      ></bug-report>
    </transition>
  </div>
</template>

<script>
import BugReport from './components/BugReport.vue'
export default {
  name: 'App',
  components: { BugReport },
  data: function () {
    return {
      openBugReport: false,
    }
  },
}
</script>

<style lang="scss">
@import 'assets/scss/app';

.is-rounded img {
  border-radius: 300000px;
}

figure {
  margin-right: 0.5rem;
}

.is-leveled {
  justify-content: space-between;
}
</style>
