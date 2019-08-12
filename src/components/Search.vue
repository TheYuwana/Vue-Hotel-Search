<template>
  <div class="search">

    <input v-model="searchValue" type="text" />
    <button @click="buttonAction">Search</button>

  </div>
</template>

<script>
export default {
  name: 'Search',
  data () {
    return {
      searchValue: ''
    }
  },
  methods: {
    buttonAction () {
      this.$emit('button-action', this.searchValue)
    }
  }
}
</script>

<style scoped lang="scss">

.search{

  display: flex;
  margin: 15px;

  input{
    width: 300px;
    display: inline;
    padding: 5px;
  }
  button{
    display: inline;
    padding: 5px;
  }
}

</style>
