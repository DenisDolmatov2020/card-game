<template>
  <div class="container">
    <div class="flip-boxes">
      <div
          v-for="n in 4"
          :key="n"
          :class="[
              'flip-box',
              { 'flip-box--flipped': n === 3 && isFlipped },
              { 'flip-box--middle': n === 3 }
          ]"
      >
        <div class="flip-box__front">
        </div>
        <div
            v-if="n === 3"
            class="flip-box__back"
        >
          <div class="flip-box__back-top">
            <div class="flip-box__back-top__value">
              <div>7</div>
              <div>&#9829;</div>
            </div>

          </div>
          <div class="flip-box__back-middle">
            &#9829;
          </div>

          <div class="flip-box__back-bottom">
            <div class="flip-box__back-bottom__value">
              <div>7</div>
              <div>&#9829;</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <UIButton
      :is-flip="isFlipped"
      @click="toggleFlip"
    />
  </div>

</template>
<script setup lang="ts">
import { ref } from 'vue';
import UIButton from './UIButton.vue';

const isFlipped = ref(false);

const toggleFlip = () => {
  isFlipped.value = !isFlipped.value;
};
</script>
<style scoped>
.container {
  margin-top: 250px;
  max-width: 100vw;
  flex-direction: column;
  justify-content: end;
  align-items: center;
  gap: 5rem;
}

.flip-boxes {
  display: flex;
  justify-content: center;
  gap: 2vw;
  margin: 0 auto;
}

.flip-box {
  top: 0;
  display: flex;
  align-content: stretch;
  width: 30vw;
  max-width: 200px;
  max-height: 240px;
  height: 36vw;
  flex-wrap: wrap;
  position: relative;
  padding: 0;
  border-top: 0;
  -webkit-perspective: 1000px;
  perspective: 1000px;
  -webkit-transition: transform 1s;
  transition: transform 1s;
}

.flip-box--middle {
  position: absolute;
  top: 245px;
  z-index: 11;
}

.flip-box--flipped {
  transform: translateY(-100%);
}

.flip-box__front,
.flip-box__back {
  position: relative;
  background-image: linear-gradient(45deg, #ffffff 3px, red 3px, red 5px, #ffffff 5px),
                    linear-gradient(-45deg, #ffffff 3px, red 3px, red 5px, #ffffff 5px);
  background-size: 4px 4px;
  border-radius: 8px;
  flex: 0 0 100%;
  -webkit-transition: all 1s .1s cubic-bezier(.5,1,.5,1);
  transition: all 1s .1s cubic-bezier(.5,1.3,.5,1.3);
  transform-style: preserve-3d;
  background-position: center;
  color: red;
}

.flip-box--flipped .flip-box__back {
  transform: rotateY(0deg);
  z-index: 10;
}

.flip-box--flipped .flip-box__front {
  transform: rotateY(180deg);
  z-index: -1;
  box-shadow: 0 0 10px black;
}

.flip-box__back {
  background: #ffffff;
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 100%;
  z-index: -1;
  transform: rotateY(-180deg);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  flex-grow: initial;
}

.flip-box__back-top,
.flip-box__back-bottom {
  height: 1em;
  font-size: 1.5em;
}

.flip-box__back-bottom {
  width: 100%;
  display: flex;
  justify-content: end;
}

.flip-box__back-top__value,
.flip-box__back-bottom__value {
  padding: 1vh;
}

.flip-box__back-bottom__value {
  transform: rotate(180deg);
}

.flip-box__back-middle {
  width: 100%;
  height: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 4em;
}

.flip-box__front {
  z-index: 11;
  box-shadow: 0 0 0 black;
}
</style>
