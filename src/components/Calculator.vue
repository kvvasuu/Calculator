<template>
  <div class="calculator-outer">
    <div class="calculator-inner">
      <div class="display">
        <div class="display-memory">{{ memory }}</div>
        <div class="display-main">{{ formatInput }}</div>
      </div>
      <div class="buttons">
        <button class="btn btn-option" id="ac" @click="clear">
          {{ clearButton }}
        </button>
        <button class="btn btn-option" id="sign" @click="signChange">
          ⁺∕₋
        </button>
        <button class="btn btn-option" id="percent" @click="percent">
          &#65285;
        </button>
        <button
          class="btn btn-color"
          id="division"
          value="/"
          @click="operation($event.target.value)"
        >
          &div;
        </button>
        <button class="btn" id="7" @click="append($event.target.id)">7</button>
        <button class="btn" id="8" @click="append($event.target.id)">8</button>
        <button class="btn" id="9" @click="append($event.target.id)">9</button>
        <button
          class="btn btn-color"
          id="times"
          value="*"
          @click="operation($event.target.value)"
        >
          &#10005;
        </button>
        <button class="btn" id="4" @click="append($event.target.id)">4</button>
        <button class="btn" id="5" @click="append($event.target.id)">5</button>
        <button class="btn" id="6" @click="append($event.target.id)">6</button>
        <button
          class="btn btn-color"
          id="minus"
          value="-"
          @click="operation($event.target.value)"
        >
          &minus;
        </button>
        <button class="btn" id="1" @click="append($event.target.id)">1</button>
        <button class="btn" id="2" @click="append($event.target.id)">2</button>
        <button class="btn" id="3" @click="append($event.target.id)">3</button>
        <button
          class="btn btn-color"
          id="plus"
          value="+"
          @click="operation($event.target.value)"
        >
          +
        </button>
        <button class="btn btn-long" id="0" @click="append($event.target.id)">
          <div class="inner-btn-long">0</div>
        </button>
        <button class="btn" id="dot" @click="dot">.</button>
        <button class="btn btn-color" id="equal" @click="solve">=</button>
      </div>
    </div>
  </div>
</template>

<script>
import click from "../assets/click.wav";
export default {
  name: "CalculatorDisplay",
  data() {
    return {
      input: "",
      memory: "",
      isOperating: false,
      isSolved: false,
    };
  },
  watch: {
    input() {
      this.input = String(this.input);
      this.playSound();
      console.log(this.input);
      console.log(this.memory);
    },
  },
  methods: {
    clear() {
      this.input = "";
      this.memory = "";
      this.isOperating = false;
    },
    signChange() {
      if (this.input) {
        this.input = -this.input;
      }
    },
    percent() {
      if (this.input) {
        this.input = Number(this.input) / 100;
      }
    },
    dot() {
      if (this.input.indexOf(".") === -1) {
        this.append(".");
      }
    },
    append(number) {
      if (this.isOperating) {
        this.input = "";
        this.isOperating = false;
      }
      if (this.input == "0" && number == "0") {
        return;
      } else {
        this.input = this.input + number;
      }
    },
    operation(symbol) {
      if (this.isOperating == false) {
        this.memory += this.input + symbol;
        this.input = "";
        this.isOperating = true;
      }
    },
    solve() {
      if (this.isOperating == false) {
        this.input = eval(this.memory + this.input);
      }
    },
    playSound() {
      const audio = new Audio(click);
      audio.play();
    },
  },
  computed: {
    formatInput() {
      if (this.input.length > 6) {
        return Number.parseFloat(this.input).toExponential(2);
      }
      return this.input;
    },
    clearButton() {
      return this.memory ? "C" : "AC";
    },
  },
};
</script>

<style>
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

.display-memory {
  font-size: 2rem;
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
</style>
