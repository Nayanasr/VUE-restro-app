<template>
  <li>
    <h2>{{ name }} {{ isFavourite ? "(Favourite)" : "" }}</h2>
    <button @click="toggleFavourite">Toggle Favourite</button>
    <button @click="toggleDetails">
      {{ displayDetails ? "Hide" : "Show" }}Details
    </button>
    <ul v-if="displayDetails">
      <li><strong>Description:</strong>{{ description }}</li>
      <li><strong>Price:</strong>{{ price }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  emits: ["toggleFavouriteStatus"],
  //   props: ["name", "description", "price", "isFavourite"],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    price: {
      type: Number,
      required: true,
    },
    isFavourite: {
      type: Boolean,
      required: false,
    },
  },
  data() {
    return {
      //   dishIsFavourite: this.isFavourite,
      displayDetails: false,
    };
  },
  methods: {
    toggleFavourite() {
      //   if (this.dishIsFavourite) {
      //     this.dishIsFavourite = false;
      //   } else {
      //     this.dishIsFavourite = true;
      //   }
      //   this.dishIsFavourite = !this.dishIsFavourite;
      this.$emit("toggleFavouriteStatus", this.id);
    },
    toggleDetails() {
      this.displayDetails = !this.displayDetails;
    },
  },
};
</script>

<style>
li {
  list-style-type: none;
}
</style>