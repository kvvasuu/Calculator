<template>
  <div class="frame-outer">
    <div class="line-horizontal-top"></div>
    <div class="line-horizontal-bottom"></div>
    <div class="frame">
      <div class="speaker">
        <div class="speaker-inner"></div>
      </div>
      <div class="frame-inner">
        <div class="line-vertical-l"></div>
        <div class="line-vertical-r"></div>
        <div class="side-button"></div>
        <div class="side-button-left"></div>
        <div class="side-button-left-clicker"></div>
        <div class="notch">
          <div class="lens">
            <div class="lens-inner">
              <div class="lens-inner-reflection"></div>
            </div>
          </div>
        </div>
        <div class="display-frame">
          <calculator-display v-show="showCalc"></calculator-display>
          <settings-display v-if="showSettings"></settings-display>
        </div>
      </div>
    </div>
  </div>
  <button @click="toggleDisplay" class="settings-btn">
    <div class="settings-btn-lines">
      <div class="settings-line"></div>
      <div class="settings-line"></div>
      <div class="settings-line"></div>
    </div>

    <p>Settings</p>
  </button>
</template>

<script>
import CalculatorDisplay from "./components/Calculator.vue";
import SettingsDisplay from "./components/Settings.vue";

export default {
  name: "App",
  components: {
    CalculatorDisplay,
    SettingsDisplay,
  },
  data() {
    return {
      showSettings: false,
      showCalc: true,
    };
  },
  methods: {
    toggleDisplay() {
      this.showSettings = !this.showSettings;
      this.showCalc = !this.showCalc;
    },
  },
};
</script>

<style>
/* CALCULATOR CONTAINER - APP*/

@font-face {
  font-family: "SFpro";
  src: url(./assets/SF-Pro.ttf);
}

* {
  font-family: "SFpro";
}

/* SETTINGS BUTTON */
.settings-btn {
  position: fixed;
  left: 1.3rem;
  bottom: 1.3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  height: 4.75rem;
  color: var(--grey);
  background-color: rgba(255, 255, 255, 0.1);
  border: none;
  border-radius: 3rem;
  margin: 0.5rem;
  z-index: 3;
}
.settings-btn p {
  display: none;
  color: rgba(255, 255, 255, 0.4);
}

.settings-btn-lines {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin: 0 0.625rem 0 0.625rem;
}

.settings-btn:hover {
  transition: 200ms;
  transform: translateY(-1px);
  background-color: var(--grey-dark);
  box-shadow: 0 0 0.3rem var(--grey-dark);
}

.settings-btn:active {
  background-color: var(--grey);
  box-shadow: 0 0 0.3rem var(--grey);
}

.settings-line {
  background-color: rgba(255, 255, 255, 0.3);
  border-radius: 1rem;
  width: 2.5rem;
  height: 0.4rem;
  margin: 0.26rem;
}

@media screen and (max-width: 700px) {
  .settings-btn {
    position: inherit;
    margin-bottom: 3rem;
  }
  .settings-btn p {
    display: block;
    margin: 0 1rem 0 0.5rem;
  }
}
</style>
