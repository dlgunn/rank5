<template>
  <div class="home">
    <div class="content-box">
      <top-five></top-five>
    </div>
  </div>
</template>

<script>
//import Vue from "vue-class-component";
// import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import TopFive from "@/components/TopFive.vue";

export default {
  components: {
    TopFive,
  },
  data: function () {
    return {
      data: [
        {
          name: "name",
        },
      ],
    };
  },
};
</script>

<style scoped>
.home {
  display: flex;
  justify-content: center;
  padding: 4px;
}
</style>
