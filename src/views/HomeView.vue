<template>
  <div class="home">
    <RatingBar />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import RatingBar from "@/components/RatingBar.vue";

@Options({
  components: {
    HelloWorld,
    RatingBar,
  },
})
export default class HomeView extends Vue {}
</script>

<style lang="scss" scoped></style>
