<template>
  <div class="home">
    <Header msg="Skill Based Team Generator"></Header>
    <div class="player-container"></div>
    <RatingBar />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Header from "@/components/SubmitPlayerHeader.vue";
import RatingBar from "@/components/RatingBar.vue"; // @ is an alias to /src
import "@/assets/style.scss";
@Options({
  components: {
    Header,
    RatingBar,
  },
})
// eslint-disable-next-line prettier/prettier
export default class HomeView extends Vue { }
</script>
<style scoped lang="scss">
@use "../assets/style.scss";

.player-container {
  margin-top: 80px;
  margin-left: 232px;
  margin-right: 232px;
  height: 856px;
  background-color: #fafafa;
}
</style>
