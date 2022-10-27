<script setup lang="ts">
import { ref } from "vue";
interface Restaurant {
  name?: string;
  address?: string;
  status?: RestaurantStatus;
  dishes?: Dish[];
}
// interface Dish {
//   china;
//   europe;
// }
interface RestInput {
  labelFor: string;
  name: string;
  model: string | undefined;
  id: string;
}
type RestaurantStatus = "Whant to try" | "Recommended";
const statusList = ["Whant to try", "Recommended"];
const restaurantList = ref<Restaurant[]>([]);
const newRestaurant = ref<Restaurant>({});
function addRestaurant() {
  restaurantList.value.push({
    name: newRestaurant.value.name,
    address: newRestaurant.value.address,
    status: newRestaurant.value.status,
    dishes: newRestaurant.value.dishes,
  });
}
const inputList = ref<RestInput[]>([
  {
    labelFor: "name",
    name: "Restaurant name",
    model: "name",
    id: "name",
  },
  {
    labelFor: "address",
    name: "Restaurant address",
    model: "address",
    id: "address",
  },
]);
</script>

<template>
  <main>
    <form @submit.prevent="addRestaurant" class="form">
      <div v-for="item in inputList" :key="item.id" class="form__item-wrapper">
        <label :for="item.labelFor">{{ item.name }}</label>
        <input v-model="newRestaurant[item.model]" :id="item.id" type="text" />
      </div>
      <div class="form__item-wrapper">
        <label for="status">Restaurant status</label>
        <select v-model="newRestaurant.status" id="status">
          <option v-for="item in statusList" :key="item" :value="item">
            {{ item }}
          </option>
        </select>
      </div>
      <button type="submit">Add Restaurant</button>
    </form>
    <ul>
      <li v-for="restaurant in restaurantList" :key="restaurant">
        {{ restaurant }}
      </li>
    </ul>
  </main>
</template>
<style scoped>
form {
  display: block;
  padding: 5px;
}
.form__item-wrapper {
  display: grid;
  gap: var(--space);
  grid-template-columns: 1fr 3fr;
  margin-bottom: var(--space);
}
</style>
