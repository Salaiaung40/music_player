<template>
<div id="musicbars">
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>

</div>
</template>

<script>
export default {

}
</script>

<style  scoped>
#musicbars {
  margin: 5em 0em 0em 30%;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 5;
}
.bar {
  /*background: #cc2e5d;*/
  background-color: #333;
  background: #fff;
  bottom: 0.1em;
  height: 3em;
  position: absolute;
  width: 0.3em;

  animation: sound 0ms -800ms linear infinite alternate;
}

@keyframes sound {
  0% {
    opacity: 0.35;
    height: 5px;
  }
  100% {
    opacity: 1;
    height: 65px;
  }
}

.bar:nth-child(1) {
  left: 1px;
  animation-duration: 474ms;
}
.bar:nth-child(2) {
  left: 7px;
  animation-duration: 433ms;
}
.bar:nth-child(3) {
  left: 13px;
  animation-duration: 407ms;
}
.bar:nth-child(4) {
  left: 20px;
  animation-duration: 458ms;
}
.bar:nth-child(5) {
  left: 26px;
  animation-duration: 400ms;
}
.bar:nth-child(6) {
  left: 32px;
  animation-duration: 427ms;
}
.bar:nth-child(7) {
  left: 38px;
  animation-duration: 441ms;
}
.bar:nth-child(8) {
  left: 44px;
  animation-duration: 419ms;
}
.bar:nth-child(9) {
  left: 50px;
  animation-duration: 487ms;
}
.bar:nth-child(10) {
  left: 57px;
  animation-duration: 442ms;
}

.bar:nth-child(11) {
  left: 63px;
  animation-duration: 474ms;
}
.bar:nth-child(12) {
  left: 69px;
  animation-duration: 433ms;
}
.bar:nth-child(13) {
  left: 75px;
  animation-duration: 407ms;
}
.bar:nth-child(14) {
  left: 81px;
  animation-duration: 458ms;
}
.bar:nth-child(15) {
  left: 87px;
  animation-duration: 400ms;
}
.bar:nth-child(16) {
  left: 93px;
  animation-duration: 427ms;
}
.bar:nth-child(17) {
  left: 99px;
  animation-duration: 441ms;
}
.bar:nth-child(18) {
  left: 105px;
  animation-duration: 419ms;
}
.bar:nth-child(19) {
  left: 111px;
  animation-duration: 487ms;
}
.bar:nth-child(20) {
  left: 117px;
  animation-duration: 442ms;
}
.bar:nth-child(21) {
  left: 123px;
  animation-duration: 442ms;
}
.bar:nth-child(22) {
  left: 129px;
  animation-duration: 433ms;
}
.bar:nth-child(23) {
  left: 135px;
  animation-duration: 407ms;
}
.bar:nth-child(24) {
  left: 141px;
  animation-duration: 458ms;
}
.bar:nth-child(25) {
  left: 147px;
  animation-duration: 400ms;
}
.bar:nth-child(26) {
  left: 153px;
  animation-duration: 427ms;
}
.bar:nth-child(27) {
  left: 159px;
  animation-duration: 441ms;
}
.bar:nth-child(28) {
  left: 165px;
  animation-duration: 419ms;
}
.bar:nth-child(29) {
  left: 171px;
  animation-duration: 487ms;
}
.bar:nth-child(30) {
  left: 177px;
  animation-duration: 442ms;
}

</style>
