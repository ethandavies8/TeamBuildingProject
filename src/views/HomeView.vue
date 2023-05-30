<template>
  <div class="home">
    <Header msg="Skill Based Team Generator"></Header>
    <div class="teams-container">
      <div class="player-info">
        <h3 class="enter-player-name">Enter Player name:</h3>
        <RatingBar class="player-rating" />
      </div>
    </div>
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

.teams-container {
  margin-top: 80px;
  margin-left: 232px;
  margin-right: 232px;
  height: 856px;
  background-color: #fafafa;
}

.player-info {
  flex-direction: row;
}
</style>
