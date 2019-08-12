<template>
  <div class="filterButton" @click="buttonAction()">
    <img :src="getIcon()">

    <img class="directionArrow" v-show="active" :src="getDirection()">
  </div>
</template>

<script>
import ArrowUpSvg from '@/assets/arrow-up.svg'
import ArrowDownSvg from '@/assets/arrow-down.svg'
import StarSvg from '@/assets/star.svg'

export default {
  name: 'FilterButton',
  props: {
    icon: {
      type: String,
      default: ""
    }
  },
  data () {
    return {
      active: false,
      direction: ""
    }
  },
  methods: {
    getIcon(){
      switch(this.$props.icon){
        case "rating":
          return StarSvg;
        break;
      }
    },
    getDirection(){
      switch(this.direction){
        case "asc":
          return ArrowUpSvg;
        break;
        case "desc":
          return ArrowDownSvg;
        break;
      }
    },
    buttonAction () {

      if(this.direction != ""){
        if(this.direction === "asc"){
          this.direction = "desc";
        }else{
          this.direction = "asc";
        }
      }else{
        this.active = true;
        this.direction = "desc";
      }

      this.$emit("button-action", {
        direction: this.direction,
        type: this.$props.icon
      })
    }
  }
}
</script>

<style scoped lang="scss">

.filterButton{

  width: 25px;
  height: 25px;
  position: relative;
  cursor: pointer;

  img{
    width: 25px;
    height: 25px;
  }

  .directionArrow{
    position: absolute;
    top: 5px;
    left: 25px;
    width: 20px;
    height: 18px;
  }
}

</style>
