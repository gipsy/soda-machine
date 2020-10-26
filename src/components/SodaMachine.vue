<template>
  <div>
    <div class="sodaMachine">
      <div class="sodaMachine__selectWrapper">
        <div class="hidden">
          <audio controls autobuffer id="preparing" autostart="false">
            <source src="../assets/wavs/soda-machine-preparing.mp3" type="audio/mpeg">
          </audio>
          <audio controls autobuffer id="pouring" autostart="false">
            <source src="../assets/wavs/soda-machine-pouring.mp3" type="audio/mpeg">
          </audio>
        </div>
        <div class="sodaMachine__state">
          {{ !state.isIdle 
          ? `Наливаю ${
            state.selectedDrink === 'dushes' && '«Дюшес»' 
            || state.selectedDrink === 'lemonad' && '«Лимонад»'
            || state.selectedDrink === 'tarhun' && '«Тархун»'
          } ...` : 'Выберите напиток ...' }}
        </div>
        <div class="sodaMachine__drinkWrapper">
          <div 
            class="sodaMachine__dushes"
            v-on="state.isIdle ? { click: () => state.selectedDrink = 'dushes' } : {}"
            :class="state.selectedDrink === 'dushes' ? 'active' : ''"
          >
            <svg class="sodaMachine__dushes__indicator" fill="#f3a133" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 1000 1000" enable-background="new 0 0 1000 1000" xml:space="preserve">
              <g><g transform="translate(0.000000,512.000000) scale(0.100000,-0.100000)"><path d="M5176.8,4982.9c-138.4-50-274.8-153.7-357.5-274.8c-132.6-192.2-134.5-205.6-142.2-1055.1l-5.8-764.9l-1181.9-3.8c-1145.4-5.8-1183.9-7.7-1210.8-42.3c-21.1-28.8-26.9-113.4-26.9-369v-332.5l50-38.4l51.9-40.4l2669.4,3.8c2617.5,5.8,2671.3,5.8,2698.2,42.3c21.2,28.8,26.9,113.4,26.9,365.1c0,180.6-7.7,338.2-15.4,349.8c-40.4,61.5-96.1,65.3-1251.1,65.3h-1155v730.3v730.3l48,23.1c38.4,17.3,197.9-13.5,974.4-194.1c511.2-117.2,951.3-213.3,978.2-213.3c76.9,0,103.8,50,157.6,284.4c63.4,269.1,55.7,297.9-86.5,338.2c-55.7,17.3-497.7,121.1-982.1,232.5C5461.2,5038.6,5367.1,5052.1,5176.8,4982.9z"/><path d="M2590,1577.4c5.8-34.6,169.1-1443.3,363.2-3128.7c196-1685.4,365.2-3088.4,376.7-3117.2c40.4-98,86.5-111.5,378.6-111.5h269.1l67.3,159.5c153.8,357.5,263.3,749.5,334.4,1176.2c38.4,242.1,48,989.7,17.3,1729.6c-26.9,682.3,46.1,1199.2,261.4,1845c151.8,459.3,463.2,1128.1,684.2,1466.4l26.9,42.3H3975.7H2580.4L2590,1577.4z"/><path d="M6871.9,1494.8C6504.8,1085.4,6057,468.5,5809.1,30.3c-322.9-572.7-559.2-1228.1-643.8-1793.1c-17.3-111.5-40.3-430.5-50-711.1c-11.5-280.6-28.8-620.8-38.4-759.1c-36.5-445.9-169.1-1001.3-334.4-1393.3l-65.3-153.8h951.3h951.3l53.8,53.8c30.7,30.8,59.6,84.6,65.4,121.1c13.4,73,722.6,6186.4,722.6,6221c0,15.4-63.4,23.1-209.5,23.1h-211.4L6871.9,1494.8z"/></g></g>
            </svg>
            <span class="sodaMachine__dushes__text">Дюшес</span>
          </div>
          <div 
            class="sodaMachine__lemonad"
            v-on="state.isIdle ? { click: () => state.selectedDrink = 'lemonad' } : {}"
            :class="state.selectedDrink === 'lemonad' ? 'active' : ''"
          >
            <svg class="sodaMachine__lemonad__indicator" fill="#b8b633" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 1000 1000" enable-background="new 0 0 1000 1000" xml:space="preserve">
              <g><g transform="translate(0.000000,512.000000) scale(0.100000,-0.100000)"><path d="M5176.8,4982.9c-138.4-50-274.8-153.7-357.5-274.8c-132.6-192.2-134.5-205.6-142.2-1055.1l-5.8-764.9l-1181.9-3.8c-1145.4-5.8-1183.9-7.7-1210.8-42.3c-21.1-28.8-26.9-113.4-26.9-369v-332.5l50-38.4l51.9-40.4l2669.4,3.8c2617.5,5.8,2671.3,5.8,2698.2,42.3c21.2,28.8,26.9,113.4,26.9,365.1c0,180.6-7.7,338.2-15.4,349.8c-40.4,61.5-96.1,65.3-1251.1,65.3h-1155v730.3v730.3l48,23.1c38.4,17.3,197.9-13.5,974.4-194.1c511.2-117.2,951.3-213.3,978.2-213.3c76.9,0,103.8,50,157.6,284.4c63.4,269.1,55.7,297.9-86.5,338.2c-55.7,17.3-497.7,121.1-982.1,232.5C5461.2,5038.6,5367.1,5052.1,5176.8,4982.9z"/><path d="M2590,1577.4c5.8-34.6,169.1-1443.3,363.2-3128.7c196-1685.4,365.2-3088.4,376.7-3117.2c40.4-98,86.5-111.5,378.6-111.5h269.1l67.3,159.5c153.8,357.5,263.3,749.5,334.4,1176.2c38.4,242.1,48,989.7,17.3,1729.6c-26.9,682.3,46.1,1199.2,261.4,1845c151.8,459.3,463.2,1128.1,684.2,1466.4l26.9,42.3H3975.7H2580.4L2590,1577.4z"/><path d="M6871.9,1494.8C6504.8,1085.4,6057,468.5,5809.1,30.3c-322.9-572.7-559.2-1228.1-643.8-1793.1c-17.3-111.5-40.3-430.5-50-711.1c-11.5-280.6-28.8-620.8-38.4-759.1c-36.5-445.9-169.1-1001.3-334.4-1393.3l-65.3-153.8h951.3h951.3l53.8,53.8c30.7,30.8,59.6,84.6,65.4,121.1c13.4,73,722.6,6186.4,722.6,6221c0,15.4-63.4,23.1-209.5,23.1h-211.4L6871.9,1494.8z"/></g></g>
            </svg>
            <span class="sodaMachine__lemonad__text">Лимонад</span>
          </div>
          <div 
            class="sodaMachine__tarhun"
            v-on="state.isIdle ? { click: () => state.selectedDrink = 'tarhun' } : {}"
            :class="state.selectedDrink === 'tarhun' ? 'active' : ''"
          >
            <svg class="sodaMachine__tarhun__indicator" fill="#418107" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 1000 1000" enable-background="new 0 0 1000 1000" xml:space="preserve">
              <g><g transform="translate(0.000000,512.000000) scale(0.100000,-0.100000)"><path d="M5176.8,4982.9c-138.4-50-274.8-153.7-357.5-274.8c-132.6-192.2-134.5-205.6-142.2-1055.1l-5.8-764.9l-1181.9-3.8c-1145.4-5.8-1183.9-7.7-1210.8-42.3c-21.1-28.8-26.9-113.4-26.9-369v-332.5l50-38.4l51.9-40.4l2669.4,3.8c2617.5,5.8,2671.3,5.8,2698.2,42.3c21.2,28.8,26.9,113.4,26.9,365.1c0,180.6-7.7,338.2-15.4,349.8c-40.4,61.5-96.1,65.3-1251.1,65.3h-1155v730.3v730.3l48,23.1c38.4,17.3,197.9-13.5,974.4-194.1c511.2-117.2,951.3-213.3,978.2-213.3c76.9,0,103.8,50,157.6,284.4c63.4,269.1,55.7,297.9-86.5,338.2c-55.7,17.3-497.7,121.1-982.1,232.5C5461.2,5038.6,5367.1,5052.1,5176.8,4982.9z"/><path d="M2590,1577.4c5.8-34.6,169.1-1443.3,363.2-3128.7c196-1685.4,365.2-3088.4,376.7-3117.2c40.4-98,86.5-111.5,378.6-111.5h269.1l67.3,159.5c153.8,357.5,263.3,749.5,334.4,1176.2c38.4,242.1,48,989.7,17.3,1729.6c-26.9,682.3,46.1,1199.2,261.4,1845c151.8,459.3,463.2,1128.1,684.2,1466.4l26.9,42.3H3975.7H2580.4L2590,1577.4z"/><path d="M6871.9,1494.8C6504.8,1085.4,6057,468.5,5809.1,30.3c-322.9-572.7-559.2-1228.1-643.8-1793.1c-17.3-111.5-40.3-430.5-50-711.1c-11.5-280.6-28.8-620.8-38.4-759.1c-36.5-445.9-169.1-1001.3-334.4-1393.3l-65.3-153.8h951.3h951.3l53.8,53.8c30.7,30.8,59.6,84.6,65.4,121.1c13.4,73,722.6,6186.4,722.6,6221c0,15.4-63.4,23.1-209.5,23.1h-211.4L6871.9,1494.8z"/></g></g>
            </svg>
            <span class="sodaMachine__tarhun__text">Тархун</span>
          </div>
        </div>
      </div>

      <div class="sodaMachine__cacheWrapper">
        <div class="sodaMachine__cache">
          У вас ₴{{ state.cache }}
        </div>
      </div>

      <div class="sodaMachine__outputWrapper">
        <div class="sodaMachine__output">
          <div class="sodaMachine__output__glass">
            <div class="sodaMachine__output__glass--inner" id="drink"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, watch, computed } from 'vue'
export default {
  name: 'SodaMachine',
  props: {
  },
  setup() {
    let state = reactive({
      selectedDrink: null,
      cache: 200,
      drinkColor: null,
      isIdle: true
    })

    const LightenColor = (color, percent) => {
      var num = parseInt(color.replace('#',''), 16),
      amt = Math.round(2.55 * percent),
      R = (num >> 16) + amt,
      B = (num >> 8 & 0x00FF) + amt,
      G = (num & 0x0000FF) + amt;

      return (0x1000000 + (R<255?R<1?0:R:255)*0x10000 + (B<255?B<1?0:B:255)*0x100 + (G<255?G<1?0:G:255)).toString(16).slice(1).replace (/^/,'#');
    };

    const prepareDrink = () => {
      state.isIdle = false
      playSound('preparing')
    }

    const poureDrink = () => {
      const drinkEl = document.getElementById('drink')

      drinkEl.classList.add('active')
      playSound('pouring')
      setTimeout(() => {
        drinkEl.classList.remove('active')
        state.selectedDrink = null
        state.isIdle = true
      }, 9000)
    }

    const playSound = ( soundname ) => {
      var thissound = document.getElementById( soundname );
      console.log(thissound)
      thissound.play();
    }

    watch(() => state.selectedDrink,
      (val) => {
        if (state.cache > 0) {
          if (val === 'dushes') { 
            state.drinkColor = '#f3a133' 
            setTimeout(() => {
              state.cache = state.cache - 5
            }, 3500)
          }
          if (val === 'lemonad') { 
            state.drinkColor = '#b8b633'
            setTimeout(() => {
              state.cache = state.cache - 7
            }, 3500)
          }
          if (val === 'tarhun') { 
            state.drinkColor = '#418107'
            setTimeout(() => {
              state.cache = state.cache - 15
            }, 3500)
          }

          if (val !== null) {
            prepareDrink()
            setTimeout(() => {
              poureDrink()
            }, 5000)
          }
        }
      }
    )

    return {
      state,
      drinkColor: computed(() => state.drinkColor),
      drinkColorLighten: computed(() => state.drinkColor && LightenColor(state.drinkColor, 20))
    }
  }
}
</script>

<style lang="scss" vars="{ drinkColor, drinkColorLighten }">
%drink-block {
  width: 100px;
  height: 100px;
  display: inline-flex;
  align-self: center;
  transition: 1s box-shadow;
}

%drink-inner {
  display: flex;
  justify-content: center;
  flex-direction: column-reverse;
  cursor: pointer;
}

.sodaMachine {
  font-size: 20px;
  background-color: red;
  width: 350px;
  height: 90vh;
  margin: 0 auto;
  border-radius: 10px;
  padding: 20px;
  position: relative;
  box-shadow: 0 -3px 20px 0px rgba(0,0,0,0.7) inset;
  &:after {
    content: '';
    position: absolute;
    height: 15px;
    border-top: 5px solid #fff;
    border-bottom: 5px solid #fff;
    width: 100%;
    left: 0;
    right: 0;
    box-shadow: 0 -3px 20px 0px rgba(0,0,0,0.7) inset;
  }
  &:after {
    bottom: 20%;
  }

  &__selectWrapper {
    border-radius: 3px;
    background-color: #d9e7e2;
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    box-shadow: inset 0 0px 15px rgba(0,0,0,.5);
    overflow: hidden;
  }

  &__drinkWrapper {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    width: 100%;
  }

  &__cacheWrapper {
    width: 100%;
    display: inline-flex;
    justify-content: flex-end;
  }

  &__cache {
    border-radius: 3px;
    background-color: #d9e7e2;
    box-shadow: inset 0 0px 15px rgba(0,0,0,.5);
    padding: 10px;
    width: 100px;
    padding: 5px 15px;
    margin-top: 20px;
  }

  &__state {
    display: flex;
  }

  &__dushes {
    @extend %drink-inner;
    display: flex;
    &__indicator {
      @extend %drink-block;
      fill: rgb(243,161,51);
      .active & {
        animation: glowing 1300ms infinite;
      }
    }
  }
  &__lemonad {
    @extend %drink-inner;
    &__indicator {
      @extend %drink-block;
      fill: rgb(184,182,51);
      .active & {
        animation: glowing 1300ms infinite;
      }
    }
  }
  &__tarhun {
    @extend %drink-inner;
    &__indicator {
      @extend %drink-block;
      fill: rgb(65,129,7);
      position: relative;
      .active & {
        animation: glowing 1300ms infinite;
      }
    }
  }

  &__outputWrapper {
    background-color: brown;
    -webkit-clip-path: polygon(50% 0%, 100% 0, 100% 35%, 50% 70%, 0 35%, 0);
    clip-path: polygon(50% 0, 100% 20%, 90% 100%, 10% 100%, 0 20%);
    width: 150px;
    height: 100px;
    display: inline-flex;
    padding: 50px 40px 10px 40px;
    margin-top: 70px;
  }

  &__output {
    border-radius: 3px;
    background-color: #fff;
    width: 100%;
    height: 100%;
    box-shadow: inset 0 -2px 10px rgba(80, 20, 20, 1);
    &__glass {
      background-color: grey;
      -webkit-clip-path: polygon(30% 25%, 70% 25%, 65% 100%, 35% 100%);
      clip-path: polygon(30% 25%, 70% 25%, 65% 100%, 35% 100%);
      width: 150px;
      height: 100px;
      top: -7px;
      position: relative;
      &--inner {
        background-color: #fff;
        top: 4px;
        left: 4px;
        -webkit-clip-path: polygon(30% 25%, 70% 25%, 65% 100%, 35% 100%);
        clip-path: polygon(30% 25%, 70% 25%, 65% 100%, 35% 100%);
        width: 142px;
        height: 92px;
        position: relative;
        &:after {
          content: '';
          background-color: var(--drinkColor);
          -webkit-clip-path: polygon(30% 25%, 70% 25%, 65% 100%, 35% 100%);
          clip-path: polygon(30% 25%, 70% 25%, 65% 100%, 35% 100%);
          height: 0;
          position: absolute;
          width: 100%;
          bottom: 0;
          left: 0;
        }
        &.active:after {
          animation: pouring 9s;
        }
      }
    }
  }
}

@-webkit-keyframes glowing {
  0% {
    fill: var(--drinkColor);
    -webkit-filter: drop-shadow( 0 0 5px var(--drinkColor));
    filter: drop-shadow( 0 0 5px var(--drinkColor));
  }
  50% {
    fill: var(--drinkColorLighten);
    -webkit-filter: drop-shadow( 0 0 15px var(--drinkColorLighten));
    filter: drop-shadow( 0 0 15px var(--drinkColor));
  }
  100% {
    fill: var(--drinkColor);
    -webkit-filter: drop-shadow( 0 0 5px var(--drinkColor));
    filter: drop-shadow( 0 0 5px var(--drinkColor));
  }
}
@keyframes glowing {
  0% {
    fill: var(--drinkColor);
    -webkit-filter: drop-shadow( 0 0 5px var(--drinkColor));
    filter: drop-shadow( 0 0 5px var(--drinkColor));
  }
  50% {
    fill: var(--drinkColorLighten);
    -webkit-filter: drop-shadow( 0 0 15px var(--drinkColorLighten));
    filter: drop-shadow( 0 0 15px var(--drinkColor));
  }
  100% {
    fill: var(--drinkColor);
    -webkit-filter: drop-shadow( 0 0 5px var(--drinkColor));
    filter: drop-shadow( 0 0 5px var(--drinkColor));
  }
}

@-webkit-keyframes pouring {
  0% {
    height: 0;
  }
  100% {
    height: 80px;
  }
}
@keyframes pouring {
  0% {
    height: 0;
  }
  100% {
    height: 80px;
  }
}
.hidden {
  display: none
}
</style>
