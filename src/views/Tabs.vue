<template>
  <div class="tabs">
    <div class="tabs__nav">
      <div
        class="tabs__nav_tab"
        v-for="tab in tabs"
        :key="tab"
        @click="selectTab(tab)"
        :class="{ 'tabs__nav_tab--active': tab.isActive }"
      >
        {{ tab.name }}
      </div>
    </div>
    <hr>
  </div>

  <slot></slot>
</template>

<script>
export default {
  data: () => {
    return {
      active: 0,
      tabs: [],
    };
  },
  // created() {
  //   console.log(this.$children);
  //   // this.tabs = this.$children;
  // },
  // mounted() {
  //   console.log("mounted " + this.$children);
  // },
  methods: {
    selectTab(selectedTab) {
      this.tabs.forEach((tab) => {
        tab.isActive = tab.name == selectedTab.name;
      });
    },
    activate(index) {
      this.active = index;
    },
  },
};
</script>

<style lang="scss" scoped>
.tabs {
  position: relative;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  background: rgb(221, 209, 208);
  padding: 1rem;
  &__nav {
    display: flex;
    &_tab {
      padding: 1rem;
      margin: 0 0.1rem 0 0;
      background: #fff;
      border-radius: 0.5rem 0.5rem 0 0;
      box-shadow: inset 0 -1rem 0.75rem -1rem rgba(0, 0, 0, 0.25);
      cursor: pointer;
      opacity: 0.75;
      transition: 100ms linear all;
      &--active {
        opacity: 1;
        box-shadow: none;
      }
    }
  }
}
</style>
