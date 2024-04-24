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
          <div class="calculator-outer">
            <div class="calculator-inner">
              <div class="display">
                <div class="display-main">20</div>
              </div>
              <div class="buttons">
                <button class="btn btn-option" id="ac">AC</button>
                <button class="btn btn-option" id="sign">⁺∕₋</button>
                <button class="btn btn-option" id="percent">&#65285;</button>
                <button class="btn btn-color" id="division">&div;</button>
                <button class="btn" id="7">7</button>
                <button class="btn" id="8">8</button>
                <button class="btn" id="9">9</button>
                <button class="btn btn-color" id="times">&#10005;</button>
                <button class="btn" id="4">4</button>
                <button class="btn" id="5">5</button>
                <button class="btn" id="6">6</button>
                <button class="btn btn-color" id="minus">&minus;</button>
                <button class="btn" id="1">1</button>
                <button class="btn" id="2">2</button>
                <button class="btn" id="3">3</button>
                <button class="btn btn-color" id="plus">+</button>
                <button class="btn btn-long" id="0">
                  <div class="inner-btn-long">0</div>
                </button>
                <button class="btn" id="dot">.</button>
                <button class="btn btn-color" id="equal">=</button>
              </div>
            </div>
            <button class="settings-btn">
              <div class="settings-line"></div>
              <div class="settings-line"></div>
              <div class="settings-line"></div>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
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

.calculator-outer {
  background-color: var(--black-light);
  color: var(--grey);
  border: none;
  border-radius: 2rem;
  width: 25rem;
  min-height: 50rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.calculator-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  margin: 1rem;
}

.display {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: flex-end;
  height: 20rem;
  width: 22.2rem;
  margin: 0 0.4 0.4 0;
  margin-bottom: 0.4rem;
}

.display-main {
  font-size: 5rem;
}

/*  BUTTONS SECTION */

.buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

/* .inner-btn {
  align-items: center;
  justify-content: center;
  text-align: center;
  margin: auto;
} */

/*  BUTTON TYPES */

.btn {
  font-size: 1.6rem;
  width: 4.75rem;
  height: 4.75rem;
  color: var(--grey);
  background-color: var(--dark);
  border: none;
  border-radius: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  text-transform: uppercase;
  margin: 0.5rem;
}

.btn:hover {
  transition: 200ms;
  transform: translateY(-1px);
  background-color: var(--grey-dark);
  box-shadow: 0 0 0.3rem var(--grey-dark);
}

.btn:active {
  background-color: var(--grey);
  color: var(--dark);
  box-shadow: 0 0 0.3rem var(--grey);
}

.btn-option {
  color: var(--black-light);
  background-color: var(--grey-dark);
}

.btn-option:hover {
  transition: 200ms;
  transform: translateY(-1px);
  background-color: rgb(189, 189, 189);
  box-shadow: 0 0 0.3rem var(--grey);
}

.btn-option:active {
  color: rgb(189, 189, 189);
  background-color: rgb(255, 255, 255);
}

.btn-long {
  width: 10.4rem;
  padding-right: 6rem;
}

.inner-btn-long {
  align-items: center;
  justify-content: center;
  text-align: center;
}

.btn-color {
  color: var(--grey);
  font-size: 1.8rem;
  background-color: color-mix(in srgb, var(--orange) 80%, transparent);
}

.btn-color:hover {
  transition: 200ms;
  transform: translateY(-1px);
  background-color: var(--orange-light);
  box-shadow: 0 0 0.3rem var(--orange);
}

.btn-color:active {
  background-color: var(--grey);
  color: var(--orange);
  box-shadow: 0 0 0.3rem var(--grey);
}

#sign {
  font-size: 1.9rem;
}

/* SETTINGS BUTTON */

.settings-btn {
  position: fixed;
  left: 1.3rem;
  bottom: 1.3rem;
  font-size: 1;
  width: 4.75rem;
  height: 4.75rem;
  color: var(--grey);
  background-color: rgba(255, 255, 255, 0.1);
  border: none;
  border-radius: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin: 0.5rem;
  z-index: 3;
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
  width: 60%;
  height: 0.4rem;
  margin: 0.26rem;
}
</style>
