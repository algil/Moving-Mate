<template>
  <div class="Switch">
    <img v-if="loading" src='~@images/loading.svg' height='22' width="22">
    <div class='container' @click.stop='changeValue' :class='{checked: value}'>
      <div class='boule'></div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";
import shortid from 'shortid';

@Component({})
export default class UISwitch extends Vue {

  @Prop() value: boolean;
  @Prop() loading: boolean;


  changeValue() {
    this.$emit('input', !this.value);
    this.$emit('switch', !this.value);
  }


  
}
</script>



<style lang='scss' scoped>

$boule: 25px;

.Switch {
  position: relative;
  display: flex;
  flex: 1 1 auto;
  justify-content: flex-end;
  align-items: center;
  padding: 5px;

  .container {
    display: flex;
    position: relative;
    width: 50px;
    height: $boule;
    border-radius: $boule;
    background-color: $w230;
    transition: all 0.2s;
    cursor: pointer;


    .boule {
      position: absolute;
      height: $boule;
      width: $boule;
      border-radius: $boule;
      background-color: white;
      box-shadow: 0 0 10px rgba(0,0,0,0.15);
      left: 0;
      top: 0;
      transition: all 0.2s;

    }

    &.checked {
      background-color: $green1;

      .boule {
        left: calc(100% - #{$boule});
      }
    }
  }

  img {
    margin-right: 10px;
  }
}

</style>

