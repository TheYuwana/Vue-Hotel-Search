<template>
  <div class="wrapper">

    <Search @button-action="searchHotels" />

    <p>Sorting:</p>
    <FilterButton icon="rating" @button-action="sortHotels" />

    <div class="hotels">
    	<HotelCard v-for="hotel in filteredHotels" :hotel="hotel" />
    </div>

  </div>
</template>

<script>
import Search from '@/components/Search.vue'
import HotelCard from '@/components/HotelCard.vue'
import FilterButton from '@/components/FilterButton.vue'

export default {
  name: 'home',
  components: {
    Search,
    HotelCard,
    FilterButton
  },
  data () {
    return {
      hotels: [
      	{
      		title: 'Playa Linda Beach Resort',
      		location: 'Oranjestad, Aruba',
      		stars: 4,
      		pricing: 209,
      		recommended: true
      	},
      	{
      		title: 'Divi Village',
      		location: 'Noord, Aruba',
      		stars: 3,
      		pricing: 309,
      		recommended: false
      	},
      	{
      		title: 'Villa Augustus',
      		location: 'Dordrecht, The Netherlands',
      		stars: 5,
      		pricing: 450,
      		recommended: false
      	},
      	{
      		title: 'Marriot Hotel',
      		location: 'Florida, USA',
      		stars: 5,
      		pricing: 999,
      		recommended: true
      	},
      	{
      		title: 'La Playa Hotel',
      		location: 'Madrid, Spain',
      		stars: 2,
      		pricing: 150,
      		recommended: false
      	}
      ],
      filteredHotels: []
    }
  },
  mounted () {
  	this.filteredHotels = this.hotels
  },
  methods: {
  	searchHotels (value) {
  		if (value === '') {
  			this.filteredHotels = this.hotels
  		} else {
  			this.filteredHotels = this.hotels.filter(hotel => {
  				return hotel.title.includes(value)
  			})
  		}
  	},
  	sortHotels(sorting){
  		if(sorting.type != ""){
  			switch(sorting.type){
  				case "rating": 
  					this.filteredHotels = this.filteredHotels.sort(function(hotA, hotB) {
  						if(sorting.direction == "asc"){
  							return hotA.stars - hotB.stars;
  						}else{
  							return hotB.stars - hotA.stars;
  						}
					});
  				break;
  			}
  		}
  	}
  }
}
</script>

<style lang="scss">
@import "../styles/config.scss";

.wrapper{

	width: 100%;

	padding: 25px;
	.hotels{
		width: 100%;
		display: flex;
		flex-wrap: wrap;
	}
}
</style>
