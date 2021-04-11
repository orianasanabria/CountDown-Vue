<template>
  <div class="counter">
    <div class="countdown">{{ start }}</div>
    <div class="buttons">
      <button
        class="btn"
        v-for="button in buttons"
        :key="button.name"
        @click="startTimer(button.value)"
      >
        {{ button.name }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      buttons: [
        { name: "3s", value: 3 },
        { name: "1m", value: 60 },
        { name: "5m", value: 300 },
        { name: "10m", value: 600 },
        { name: "30m", value: 1800 },
        { name: "1h", value: 3600 },
      ],
      name: "Timer",
      start: "00:00",
      time: "0",
      counter: "",
    };
  },

  methods: {
    startTimer(i) {
      clearInterval(this.counter);
      this.counter = setInterval(() => {
        this.time = i--;
        this.start = this.convert(this.time);

        if (this.time === 0) {
          clearInterval(this.counter);
          return;
        }
      }, 1000);
    },
    convert(sec) {
      let minutes = Math.floor(sec / 60);
      let seconds = sec % 60;
      minutes = minutes < 10 ? `0${minutes}` : minutes;
      seconds = seconds < 10 ? `0${seconds}` : seconds;
      return `${minutes}:${seconds}`;
    },
  },
};
</script>

<style lang="scss" scoped>
.counter {
  display: grid;
  place-items: center;
  min-width: 100%;
  padding: 2rem;
}

@media (min-width: 576px) {
  .counter {
    min-width: 32rem;
  }
}

.countdown {
  font-size: 5rem;
  display: grid;
  place-items: center;
  color: #fff;
  text-align: center;
  margin-bottom: 4rem;
  background-color: #1c1c1c;
  min-height: 12rem;
  width: 100%;
}

.buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.btn {
  flex: 1 1 160px;
  margin: 0.5em;
  width: 100%;

  font-size: 18px;
  font-family: "Poppins", sans-serif;
  border-radius: 5px;
  color: white;
  min-height: 4.5rem;
  min-width: 5rem;
  border: none;
  outline: none;

  &:nth-of-type(1) {
    background-color: #b31512;
    :hover {
      background-color: white;
    }
  }
  &:nth-of-type(2) {
    background-color: #e27515;
  }
  &:nth-of-type(3) {
    background-color: #6b1b9a;
  }
  &:nth-of-type(4) {
    background-color: #018290;
  }
  &:nth-of-type(5) {
    background-color: #bd095d;
  }
  &:nth-of-type(6) {
    background-color: #2f68d1;
  }
}
</style>
