<template>
  <div class="sidebar" :class="isToggled ? 'on' : 'off'">
    <button @click="toggle()">toggle</button>
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

<style>
.sidebar {
  float: left;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  bottom: 0;
  padding: 0;

  transition: 0.3s ease;

  display: flex;
  flex-direction: column;

  background-color: aqua;
  width: 300px;
}
.on {
}

.off {
  left: -300px;
}
</style>