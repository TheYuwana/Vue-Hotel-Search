<template>
  <div class="hotelCard">

    <div v-show="hotel.recommended" class="recommended">
      <img :src="recommendedSvg">
    </div>

    <img src="https://via.placeholder.com/200x150"/>

    <h3>{{ hotel.title }}</h3>
    <p>{{ hotel.location }}</p>
    <div class="stars">
      <img v-for="star in hotel.stars" :src="StarSvg">
    </div>

    <div class="price">
      <p>&euro; {{ hotel.pricing }},-</p>
    </div>

  </div>
</template>

<script>
import RecommendedSvg from '@/assets/correct-symbol.svg'
import StarSvg from '@/assets/star.svg'
export default {
  name: 'HotelCard',
  props: {
    hotel: {
      type: Object,
      default: () => {
        return {
          title: '',
          location: '',
          stars: 1,
          pricing: 0,
          recommended: false
        }
      }
    }
  },
  data () {
    return {
      recommendedSvg: RecommendedSvg,
      StarSvg: StarSvg
    }
  }
}
</script>

<style scoped lang="scss">
@import "../styles/config.scss";
.hotelCard{

  margin: 25px 25px 0px 0px;
  border: 1px solid black;
  width: 200px;
  position: relative;
  display: inline-block;

  h3{
    margin: 5px 0px;
  }

  .recommended{
    position: absolute;
    top: 5px;
    right: 13px;
    img{
      height: 50px;
      width: 50px;
    }
  }

  .stars{
    margin: 5px 0px;
    img{
      width: 15px;
    }
  }

  .price{
    border: 1px solid black;
    width: 60px;
    height: 60px;
    border-radius: 50px;
    text-align: center;
    position: absolute;
    right: -18px;
    bottom: -18px;
    background-color: #fff;
    p{
      margin-top: 20px;
    }
  }
}

</style>
