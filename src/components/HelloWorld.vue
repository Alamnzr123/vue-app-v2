<template>
  <div>
    <progress-bar
      :height="height"
      :width="width"
      :start-color="startColor"
      :inner-stroke-color="innerStrokeColor"
      :diameter="200"
      :completed-steps="completedSteps"
      :total-steps="totalSteps"
    >
    </progress-bar>
    <h1>How would you rate your satisfaction with our product?</h1>
    <div @mouseleave="showCurrentRating(0)" style="display: inline-block">
      <star-rating
        :show-rating="false"
        inactive-color="#B6B3B3"
        active-color="#474545"
        v-bind:star-size="100"
        @current-rating="showCurrentRating"
        @rating-selected="setCurrentSelectedRating"
        :increment="0.5"
      ></star-rating>
    </div>
    <div style="margin-top: 10px; font-weight: bold">{{ currentRating }}</div>
    <div>
      Very dissatified <span style="margin-left: 260px">Very satisfied</span>
    </div>
  </div>
</template>

<script type="text/javascript">
import ProgressBar from "vue2-progress-bar";
import StarRating from "vue-star-rating";

export default {
  components: {
    ProgressBar,
    StarRating,
  },
  data() {
    return {
      height: 50,
      width: 750,
      startColor: "purple",
      innerStrokeColor: "#d6efff",
      completedSteps: 2,
      totalSteps: 10,
      // rating: 3,
      rating: "No Rating Selected",
      currentRating: "No Rating",
      currentSelectedRating: "No Current Rating",
      boundRating: 3,
    };
  },
  methods: {
    setRating: function (rating) {
      this.rating = "You have Selected: " + rating + " stars";
    },
    showCurrentRating: function (rating) {
      this.currentRating =
        rating === 0 ? this.currentSelectedRating : +rating + " stars";
    },
    setCurrentSelectedRating: function (rating) {
      this.currentSelectedRating = "You have Selected: " + rating + " stars";
    },
  },
};
</script>
