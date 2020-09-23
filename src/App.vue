<template>
    <div  class="center examplex">
      <vs-navbar center-collapsed v-model="active" >
        <vs-navbar-item :active="active == 'mars'" id="mars" to="/" >
          Mars
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'inSight'" id="inSight"  to="/inSight">
          InSight
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'epic'" id="epic" to="/epic">
          Epic
        </vs-navbar-item>
      </vs-navbar>
    <div class="square pa-3" id="view">
      <router-view  class="child"/>
    </div>
    </div>

</template>

 <script>
  export default {
    data:() => ({
      active: 'mars'
    })
  }
  </script>

<style>
#view{
  background-color: #FCFCFC;
  padding-top: 50px;
  padding: 20px;
}
  
</style>