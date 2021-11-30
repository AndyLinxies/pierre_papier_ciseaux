<template>
  <div id="app">
    <!--  -->
    <div class="global">
      <div class="top grid grid-cols-1 md:grid-cols-2 text-white rounded-md">
        <div class="textes text-2xl font-extrabold">
          <p>ROCK</p>
          <p>PAPER</p>
          <p>SCISSORS</p>
        </div>
        <!-- score -->
        <div class="score">
          <p>SCORE</p>
          <p class="text-2xl font-extrabold">{{ yourScore }}</p>
          <p>COMPUTER SCORE</p>
          <p class="text-2xl font-extrabold">{{ computerScore }}</p>
        </div>
      </div>

      <!-- buttons First screen -->
      <div class="glob_btns" v-if="fighting == false">
        <!--Paper  -->
        <button
          @click="chooseWeapon('paper')"
          class="svgC hand handAbs bg-blue-100"
          :class="yourWeapon == 'paper' && 'bg-blue-400'"
          type="button"
        >
          <svg
            class="real-svg"
            xmlns="http://www.w3.org/2000/svg"
            width="49"
            height="59"
          >
            <path
              fill="#3B4262"
              d="M47.125 11.832a2.922 2.922 0 00-1.232-.198c-.57.04-1.029.271-1.302.65-1.604 2.248-2.919 6.493-3.979 9.905-.486 1.577-1.14 3.688-1.612 4.69-.493-2.807.064-13.09.28-17.05l.003-.064c.15-2.751.17-3.234.138-3.446-.238-1.509-.843-2.5-1.799-2.943-.966-.45-2.22-.25-3.572.563-.677.41-.865 1.816-1.446 8.19l-.002.028c-.32 3.502-1.058 11.566-1.965 12.91-1.023-1.88-2.431-12.555-3.039-17.176-.425-3.236-.673-5.094-.84-5.655-.35-1.176-1.83-2.176-3.295-2.232-1.22-.06-2.22.56-2.698 1.638-.894.995-.578 4.292.41 12.102.47 3.718 1.44 11.395.83 12.257-1.219-.133-3.31-4.942-6.215-14.299-.816-2.62-1.068-3.408-1.318-3.753-.494-1.202-2.172-2.129-3.676-2.024a3.183 3.183 0 00-.377.049c-.787.156-2.584.881-2.2 4.226 1.06 4.637 2.213 8.041 3.331 11.346l.023.066c.669 1.98 1.302 3.85 1.89 5.925 1.385 4.9.846 7.94.84 7.975-.046.312-.143.503-.288.57a.556.556 0 01-.195.045c-.44.03-1.098-.26-1.437-.45-.776-1.482-4.636-8.544-8.134-9.524l-.126-.037-.127.012c-1.283.121-2.226.606-2.803 1.441-.914 1.32-.535 3.002-.444 3.34l.052.12c.028.051 2.834 5.165 3.268 7.544.374 2.04 2.311 4.25 3.869 6.026l.064.073c.508.58.946 1.083 1.292 1.548 4.519 4.713 11.665 8.677 11.723 8.71.892.657 1.387 1.293 1.44 1.84a.798.798 0 01-.16.58l-.155.162.988.96 18.853-1.324.804-3.684c2.486-10.402 1.967-19.272 1.958-19.33.01-.327.706-3.483 1.266-6.033l.017-.065c1.117-5.08 2.505-11.4 2.772-13.803.116-1.028-.542-1.972-1.675-2.401z"
            />
          </svg>
        </button>
        <!-- Scissor -->
        <button
          @click="chooseWeapon('scissor')"
          class="svgC sis sisAbs bg-yellow-100"
          :class="yourWeapon == 'scissor' && 'bg-yellow-400'"
          type="button"
        >
          <svg
            class="real-svg"
            xmlns="http://www.w3.org/2000/svg"
            width="51"
            height="58"
          >
            <path
              fill="#3B4262"
              d="M13.971 25.702l6.012-8.415c-2.499-.415-7.088-.507-10.846 3.235C3.212 26.421.812 39.163.312 42.248L15.37 57.24c2.711-.232 14.713-1.827 26.279-13.34.122-.249 2.94-2.321.636-4.614-1.1-1.095-2.919-1.074-4.042.044-.572.57-1.461.577-2.021.02-.56-.557-.552-1.443.02-2.012l4.087-4.069c2.076-2.067.119-5.555-2.78-4.717l-3.345 2.851c-.611.53-1.52.439-2.022-.14-.519-.597-.408-1.503.183-2.013 11.687-10.208 9.98-8.979 17.5-15.995 2.809-2.329-.725-6.447-3.493-4.09L28.182 25.45c-.529.448-1.34.457-1.86-.02-.601-.517-.615-1.262-.222-1.85L38.787 3.944c1.854-2.5-1.795-5.277-3.749-2.757L16.28 27.307c-.452.65-1.364.8-1.985.345a1.377 1.377 0 01-.323-1.95z"
            />
          </svg>
        </button>
        <!-- Rock -->
        <button
          @click="chooseWeapon('rock')"
          class="svgC fist fistAbs bg-red-100"
          :class="yourWeapon == 'rock' && 'bg-red-400'"
          type="button"
        >
          <img
            class="real-svg"
            width="50px"
            src="./assets/images/2789573.svg"
            alt=""
          />
        </button>
      </div>

      <!-- Result Screen -->
      <div
        class="grid grid-cols-1 md:grid-cols-3 text-white mt-20"
        v-if="fighting"
      >
        <!-- LEFT Your choice -->
        <div>
          <p>YOU PICKED</p>
          <!--If you choose Rock -->
          <button
            class="svgC bg-red-100"
            :class="yourWeapon == 'rock' && 'fist'"
            v-if="yourWeapon == 'rock'"
          >
            <img
              class="real-svg ml-7"
              width="50px"
              src="./assets/images/2789573.svg"
              alt=""
            />
          </button>
          <!-- if you choose paper -->
          <button
            class="svgC bg-red-100"
            :class="yourWeapon == 'paper' && 'hand'"
            v-if="yourWeapon == 'paper'"
          >
            <svg
              class="real-svg ml-7"
              xmlns="http://www.w3.org/2000/svg"
              width="49"
              height="59"
            >
              <path
                fill="#3B4262"
                d="M47.125 11.832a2.922 2.922 0 00-1.232-.198c-.57.04-1.029.271-1.302.65-1.604 2.248-2.919 6.493-3.979 9.905-.486 1.577-1.14 3.688-1.612 4.69-.493-2.807.064-13.09.28-17.05l.003-.064c.15-2.751.17-3.234.138-3.446-.238-1.509-.843-2.5-1.799-2.943-.966-.45-2.22-.25-3.572.563-.677.41-.865 1.816-1.446 8.19l-.002.028c-.32 3.502-1.058 11.566-1.965 12.91-1.023-1.88-2.431-12.555-3.039-17.176-.425-3.236-.673-5.094-.84-5.655-.35-1.176-1.83-2.176-3.295-2.232-1.22-.06-2.22.56-2.698 1.638-.894.995-.578 4.292.41 12.102.47 3.718 1.44 11.395.83 12.257-1.219-.133-3.31-4.942-6.215-14.299-.816-2.62-1.068-3.408-1.318-3.753-.494-1.202-2.172-2.129-3.676-2.024a3.183 3.183 0 00-.377.049c-.787.156-2.584.881-2.2 4.226 1.06 4.637 2.213 8.041 3.331 11.346l.023.066c.669 1.98 1.302 3.85 1.89 5.925 1.385 4.9.846 7.94.84 7.975-.046.312-.143.503-.288.57a.556.556 0 01-.195.045c-.44.03-1.098-.26-1.437-.45-.776-1.482-4.636-8.544-8.134-9.524l-.126-.037-.127.012c-1.283.121-2.226.606-2.803 1.441-.914 1.32-.535 3.002-.444 3.34l.052.12c.028.051 2.834 5.165 3.268 7.544.374 2.04 2.311 4.25 3.869 6.026l.064.073c.508.58.946 1.083 1.292 1.548 4.519 4.713 11.665 8.677 11.723 8.71.892.657 1.387 1.293 1.44 1.84a.798.798 0 01-.16.58l-.155.162.988.96 18.853-1.324.804-3.684c2.486-10.402 1.967-19.272 1.958-19.33.01-.327.706-3.483 1.266-6.033l.017-.065c1.117-5.08 2.505-11.4 2.772-13.803.116-1.028-.542-1.972-1.675-2.401z"
              />
            </svg>
          </button>
          <!-- If you choose scissor -->
          <button
            class="svgC bg-yellow-100"
            :class="yourWeapon == 'scissor' && 'sis'"
            v-if="yourWeapon == 'scissor'"
          >
            <svg
              class="real-svg ml-7"
              xmlns="http://www.w3.org/2000/svg"
              width="51"
              height="58"
            >
              <path
                fill="#3B4262"
                d="M13.971 25.702l6.012-8.415c-2.499-.415-7.088-.507-10.846 3.235C3.212 26.421.812 39.163.312 42.248L15.37 57.24c2.711-.232 14.713-1.827 26.279-13.34.122-.249 2.94-2.321.636-4.614-1.1-1.095-2.919-1.074-4.042.044-.572.57-1.461.577-2.021.02-.56-.557-.552-1.443.02-2.012l4.087-4.069c2.076-2.067.119-5.555-2.78-4.717l-3.345 2.851c-.611.53-1.52.439-2.022-.14-.519-.597-.408-1.503.183-2.013 11.687-10.208 9.98-8.979 17.5-15.995 2.809-2.329-.725-6.447-3.493-4.09L28.182 25.45c-.529.448-1.34.457-1.86-.02-.601-.517-.615-1.262-.222-1.85L38.787 3.944c1.854-2.5-1.795-5.277-3.749-2.757L16.28 27.307c-.452.65-1.364.8-1.985.345a1.377 1.377 0 01-.323-1.95z"
              />
            </svg>
          </button>
        </div>
        <!-- MIDDLE If you win or loose -->
        <div>
          <p v-if="result !== 'draw'" class="text-2xl font-extrabold">
            You
            <span
              :class="
                result == 'won' ? 'text-green-500' : 'text-red-500'
              "
              >{{ result }}</span
            >
          </p>
          <div v-if="result == 'draw'" class="text-2xl font-extrabold">
            <p>EQUAL</p>
          </div>
          <button @click="playAgain" class="bg-white rounded-sm text-black p-3">
            PLAY AGAIN
          </button>
        </div>
        <!-- RIGHT:  Computer choice -->
        <div>
          <p>THE HOUSE PICKED</p>
          <!--If computer choose Rock -->
          <button
            class="svgC bg-red-100"
            :class="computerWeapon == 'rock' && 'fist'"
            v-if="computerWeapon == 'rock'"
          >
            <img
              class="real-svg ml-7"
              width="50px"
              src="./assets/images/2789573.svg"
              alt=""
            />
          </button>
          <!-- If computer chooses paper -->
          <button
            class="svgC bg-red-100"
            :class="computerWeapon == 'paper' && 'hand'"
            v-if="computerWeapon == 'paper'"
          >
            <svg
              class="real-svg ml-7"
              xmlns="http://www.w3.org/2000/svg"
              width="49"
              height="59"
            >
              <path
                fill="#3B4262"
                d="M47.125 11.832a2.922 2.922 0 00-1.232-.198c-.57.04-1.029.271-1.302.65-1.604 2.248-2.919 6.493-3.979 9.905-.486 1.577-1.14 3.688-1.612 4.69-.493-2.807.064-13.09.28-17.05l.003-.064c.15-2.751.17-3.234.138-3.446-.238-1.509-.843-2.5-1.799-2.943-.966-.45-2.22-.25-3.572.563-.677.41-.865 1.816-1.446 8.19l-.002.028c-.32 3.502-1.058 11.566-1.965 12.91-1.023-1.88-2.431-12.555-3.039-17.176-.425-3.236-.673-5.094-.84-5.655-.35-1.176-1.83-2.176-3.295-2.232-1.22-.06-2.22.56-2.698 1.638-.894.995-.578 4.292.41 12.102.47 3.718 1.44 11.395.83 12.257-1.219-.133-3.31-4.942-6.215-14.299-.816-2.62-1.068-3.408-1.318-3.753-.494-1.202-2.172-2.129-3.676-2.024a3.183 3.183 0 00-.377.049c-.787.156-2.584.881-2.2 4.226 1.06 4.637 2.213 8.041 3.331 11.346l.023.066c.669 1.98 1.302 3.85 1.89 5.925 1.385 4.9.846 7.94.84 7.975-.046.312-.143.503-.288.57a.556.556 0 01-.195.045c-.44.03-1.098-.26-1.437-.45-.776-1.482-4.636-8.544-8.134-9.524l-.126-.037-.127.012c-1.283.121-2.226.606-2.803 1.441-.914 1.32-.535 3.002-.444 3.34l.052.12c.028.051 2.834 5.165 3.268 7.544.374 2.04 2.311 4.25 3.869 6.026l.064.073c.508.58.946 1.083 1.292 1.548 4.519 4.713 11.665 8.677 11.723 8.71.892.657 1.387 1.293 1.44 1.84a.798.798 0 01-.16.58l-.155.162.988.96 18.853-1.324.804-3.684c2.486-10.402 1.967-19.272 1.958-19.33.01-.327.706-3.483 1.266-6.033l.017-.065c1.117-5.08 2.505-11.4 2.772-13.803.116-1.028-.542-1.972-1.675-2.401z"
              />
            </svg>
          </button>
          <!-- If computer chooses scissor -->
          <button
            class="svgC bg-yellow-100"
            :class="computerWeapon == 'scissor' && 'sis'"
            v-if="computerWeapon == 'scissor'"
          >
            <svg
              class="real-svg ml-7"
              xmlns="http://www.w3.org/2000/svg"
              width="51"
              height="58"
            >
              <path
                fill="#3B4262"
                d="M13.971 25.702l6.012-8.415c-2.499-.415-7.088-.507-10.846 3.235C3.212 26.421.812 39.163.312 42.248L15.37 57.24c2.711-.232 14.713-1.827 26.279-13.34.122-.249 2.94-2.321.636-4.614-1.1-1.095-2.919-1.074-4.042.044-.572.57-1.461.577-2.021.02-.56-.557-.552-1.443.02-2.012l4.087-4.069c2.076-2.067.119-5.555-2.78-4.717l-3.345 2.851c-.611.53-1.52.439-2.022-.14-.519-.597-.408-1.503.183-2.013 11.687-10.208 9.98-8.979 17.5-15.995 2.809-2.329-.725-6.447-3.493-4.09L28.182 25.45c-.529.448-1.34.457-1.86-.02-.601-.517-.615-1.262-.222-1.85L38.787 3.944c1.854-2.5-1.795-5.277-3.749-2.757L16.28 27.307c-.452.65-1.364.8-1.985.345a1.377 1.377 0 01-.323-1.95z"
              />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      options: ["rock", "paper", "scissor"],
      yourWeapon: "",
      computerWeapon: "",
      result: "",
      yourScore: 0,
      computerScore: 0,
      totalRounds: 0,
      fighting: false,
      // clicked:false
    };
  },
  methods: {
    
    //Recupere ce qui a été passé en param dans les boutons
    chooseWeapon(weapon) {
      this.fighting = true;
      this.yourWeapon = weapon;
      // faire console.log car bug inspecteur vue
      console.log(this.yourWeapon);
      //Logic
      //Choisis au hasard une des options via l'index du tableau option
      this.computerWeapon =
        this.options[Math.floor(Math.random() * this.options.length)];

      //Test pretend processing
      this.fighting=true
      this.pretendProcessing();
    },
    _draw() {
      (this.result = "draw"), this.totalRounds++;
    },

    _win() {
      this.result = "won";
      this.yourScore++;
      this.totalRounds++;
    },

    _lost() {
      this.result = "lost";
      this.computerScore++;
      this.totalRounds++;
    },

    playAgain() {
      this.fighting = false;
    },

    _fight(){
      if (this.yourWeapon === this.computerWeapon) this._draw();
      if (this.computerWeapon === "rock") {
        if (this.yourWeapon === "paper") {
          this._win();
        }
        if (this.yourWeapon === "scissor") {
          this._lost();
        }
      }
      if (this.computerWeapon === "paper") {
        if (this.yourWeapon === "rock") {
          this._lost();
        }
        if (this.yourWeapon === "scissor") {
          this._win();
        }
      }
      if (this.computerWeapon === "scissor") {
        if (this.yourWeapon === "rock") {
          this._win();
        }
        if (this.yourWeapon === "paper") {
          this._lost();
        }
      }
      
    },
    pretendProcessing() {
      var x = 0;
      var intervalID = setInterval(() => {
        this.computerWeapon =
          this.options[Math.floor(Math.random() * this.options.length)];

        if (++x === 10) {
          window.clearInterval(intervalID);
          this._fight();
          this.fighting = true;
        }
      }, 100);
    },
    
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html {
  background-image: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%));
  height: 100%;
}
.top {
  border: solid 1px white;
  width: 70%;
  margin-left: 16%;
}
.svgC {
  /* background-color: white; */
  width: 150px;
  height: 150px;
  padding-left: 2.5%;
}
.svgC:hover {
  background-color: gray;
}
.hand {
  border: solid 10px blue;
  border-radius: 50%;
}
.handAbs {
  position: absolute;
  top: 20%;
  right: 50%;
}
.fist {
  border: solid 10px red;
  border-radius: 50%;
}
.fistAbs {
  position: absolute;
  top: 60%;
  left: 48.5%;
}
.sis {
  border: solid 10px yellow;
  border-radius: 50%;
}
.sisAbs {
  position: absolute;
  top: 20%;
  right: 30%;
}
/* .real-svg{
  opacity: 70%;
} */
.glob_btns {
  background-image: url("./assets/images/bg-triangle.svg");
  background-repeat: no-repeat;
  background-size: 26%;
  height: 92vh;
  background-position: 55%;
  position: relative;
}
</style>
