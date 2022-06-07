<template>
  <h1 class="text-center mt-4">Computer Accessories</h1>
  <h2>
    ID: <span class="text-danger">{{ id }}</span>
  </h2>

  <table class="table table-striped">
    <thead class="bg-primary text-white">
      <tr>
        <th>Item</th>
        <th>Manufacturer</th>
        <th>Description</th>
        <th>Price</th>
        <th>Quantity</th>
      </tr>
    </thead>
    <tbody>
      <tr class="hover-list">
        <td>
          {{ computer.item }}
        </td>
        <td>
          {{ computer.manufacturer }}
        </td>
        <td>
          {{ computer.description }}
        </td>
        <td>
          {{ computer.price }}
        </td>
        <td>
          <span> <i class="flag flag-france"></i></span>
          <span> <i v-bind:class="{ flag }"></i></span>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      computer: [],
      flag: "ad",
    };
  },

  methods: {
    convertToLowerCase() {},
  },
  mounted() {
    fetch("http://127.0.0.1:8000/api/computer-items/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.computer = data))
      .then((res) => console.log(res))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
.width {
  width: 30px;
  height: 30px;
}
.hover-list:hover {
  background: rgb(226, 222, 222);
}
</style>
