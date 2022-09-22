<template>
  <h1>Little Indian Restro</h1>
  <ul>
    <dish-details
      v-for="dish in dishes"
      :key="dish.id"
      :id="dish.id"
      :name="dish.name"
      :description="dish.description"
      :price="dish.price"
      :isFavourite="dish.isFavourite"
      @toggleFavouriteStatus="toggleFavouriteStatus"
    />
  </ul>
</template>

<script>
import DishDetails from "./components/DishDetails.vue";
export default {
  name: "App",
  components: { DishDetails },
  data() {
    return {
      dishes: [
        {
          id: "avi",
          name: "Butter Chicken",
          description: "It's finger licking good",
          price: 350,
          isFavourite: true,
        },
        {
          id: "vaibhav",
          name: "Chole Bhature",
          description: "The crispy puffed bhatura and gravy",
          price: 150,
          isFavourite: false,
        },
        {
          id: "akshata",
          name: "Fish Fry",
          description: "includes french fries,coleslaw",
          price: 300,
          isFavourite: false,
        },
      ],
    };
  },
  methods: {
    //to get dishDetails from child component
    toggleFavouriteStatus(dishID) {
      // console.log("dish ID in parent", dishID);
      let identifiedDish = this.dishes.find((dish) => dish.id === dishID);
      identifiedDish.isFavourite = !identifiedDish.isFavourite;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app h1 {
  background-color: rgb(226, 43, 211);
}
</style>