<template>
  <div>
    <div :class="{ hasOpenLoading }"></div>
    <!-- {{InSight}} -->
    <div class="row" v-if="haveOpenDoad != true">
    <div class="col " v-for="item in  InSight" v-bind:key="item.index">
     <card 
        :title = "item.camera.full_name"
        :image = "item.img_src"
        :des1 = "item.earth_date"
        :des2 = "item.rover.status"
        />


  </div>
  </div>
  </div>
</template>

<script>
import card from './Card'
export default {
  data() {
    return {
      inSight:"",
       hasOpenLoading: true,
    };
  },
  components: {
    card
  },
  methods: {
    fetchInSight: function (type) {
    const loading = this.$vs.loading({
      type
    })
      this.axios
        .get("https://api.nasa.gov/insight_weather/?api_key=DEMO_KEY&feedtype=json&ver=1.0")
        .then((res) => {
          this.inSight = res.data;
          loading.close()
          this.hasOpenLoading = false
        });
    },
  },
  created() {
    this.fetchInSight('corners');
  },
};
</script>


