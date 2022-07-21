<template>
  <div class="sidebar p-2 dark-bg" :class="isToggled ? 'on' : 'off'">
    <router-link :to="{ name: 'Home', params: { src: 'all' } }" active-class="accent">
      <div
        class="menu p-2 d-flex justify-content-start align-items-center"
        style="height: 50px"
      >
        <div class="">
          <img
            src="https://img.icons8.com/material-sharp/24/FFFFFF/home.png"
            style="height: 30px"
          />
        </div>

        <div class="ps-4">
          <h5 class="menu-text">Home</h5>
        </div>
      </div>
    </router-link>

    <router-link :to="{ name: 'Home', params: { src: 'gundam' } }" active-class="accent">
      <div
        class="menu p-2 d-flex justify-content-start align-items-center"
        style="height: 50px"
      >
        <div class="">
          <img
            src="@/assets/gundam-logo.png"
            style="height: 30px"
          />
        </div>

        <div class="ps-4">
          <h5 class="menu-text">Gundam</h5>
        </div>
      </div>
    </router-link>

    <router-link :to="{ name: 'Home', params: { src: 'FAG' } }" active-class="accent">
      <div
        class="menu p-2 d-flex justify-content-start align-items-center"
        style="height: 50px"
      >
        <div class="">
          <img
            src="@/assets/fag-logo.png"
            style="height: 30px"
          />
        </div>

        <div class="ps-4">
          <h5 class="menu-text">Frame Arm Girls</h5>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isToggled: false,
    };
  },
  methods: {
    toggle() {
      this.isToggled = !this.isToggled;
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.sidebar {
  transition: 0.3s ease;
  top: 0;
  left: 0;
  bottom: 0;
  display: flex;
  flex-direction: column;
  width: 300px;
  height: 100%;
}
.on {
  left: 0;
}

.off {
  left: -300px;
  width: 60px;
}
a {
  text-decoration: none;
  color: #ffffff;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
}
a:hover {
  color: #ffffff;
}
.menu {
}
.menu:hover {
  background-color: #383838;
}
.accent {
  background-color: #383838;
}
</style>