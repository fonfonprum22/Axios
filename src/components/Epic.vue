<template>
<div>
  <div  :class="{ hasOpenLoading }">
  </div>
   <div class="row" v-if="hasOpenLoading != true">
     {{epic}}
     <div class="col " v-for="item in epic.image" v-bind:key="item.index">
     <card :data = "item"/>
     </div>
</div>
</div>
</template>


<script>
export default {
  data() {
    return {
      epic: "hello",
      hasOpenLoading: true,
    };
  },
  components: {},
  methods: {
    fetchEpic: function (type) {
       const loading = this.$vs.loading({
         type
       })
      this.axios
        .get("https://api.nasa.gov/EPIC/api/natural?api_key=DEMO_KEY")
        .then((res) => {
          this.epic = res.data;
          loading.close()
          this.hasOpenLoading = false
        });
    },
  },
  created() {
    this.fetchEpic('corners');
  },
};
</script>


<style scoped lang="stylus">
    .hasOpenLoading
      .box-loading
        opacity 0
        transform scale(.7)
    .box-loading
      width 120px
      height 120px
      position relative
      margin 5px
      border-radius 20px
      box-shadow 0px 10px 20px -10px rgba(0,0,0,.07)
      overflow hidden
      cursor pointer
      transition all .25s ease
      &:hover
        transform translate(0,-5px)
        box-shadow 0px 15px 20px -10px rgba(0,0,0,.09)
      >>>.vs-loading
        padding 0px
  </style>
