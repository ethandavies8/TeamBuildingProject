<template>
  <div class="player-rating-radio-group">
    <template v-for="item in 10" v-bind:key="item">
      <input
        name="player-1-rating"
        type="radio"
        class="player-rating-radio"
        :value="item"
        :id="'player-1-rating-' + item"
      />
      <label
        :for="'player-1-rating-' + item"
        class="player-rating-label"
      ></label>
    </template>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  components: {},
})
export default class RatingBar extends Vue {}
</script>

<style lang="scss" scoped>
.player-rating-radio-group {
  display: inline-flex;
  flex-direction: row;
}

.player-rating-radio-group .player-rating-label:first-of-type::before {
  border-top-left-radius: 12px;
  border-bottom-left-radius: 12px;
}

.player-rating-radio-group .player-rating-label:last-of-type::before {
  border-top-right-radius: 12px;
  border-bottom-right-radius: 12px;
}

.player-rating-radio {
  opacity: 0;
  display: inline-block;
  height: 0px;
  width: 0px;
  margin: 0;
}

label.player-rating-label {
  display: inline-block;
  height: 0;
  width: 0;
  padding-top: 32px;
  padding-left: 32px;
  position: relative;
}

.player-rating-label::before {
  border: 1px solid black;
  opacity: 1;
  display: block;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  content: " ";
  background-color: teal;
}

.player-rating-radio:checked + .player-rating-label::before {
  background-color: teal;
}

.player-rating-radio:checked
  ~ .player-rating-radio
  + .player-rating-label::before {
  background-color: white;
}
</style>
