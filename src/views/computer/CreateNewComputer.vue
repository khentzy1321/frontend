<template>
  <h1 class="text-center">Add Accessories</h1>

  <div class="container w-50 border border-radius p-4">
    <form @submit="postData">
      <div class="form-group">
        <label for="item">Item</label>
        <input
          type="text"
          class="form-control"
          v-model="item"
          id="item"
        />
      </div>
      <div class="form-group">
        <label for="manufacturer">Manufacturer</label>
        <input type="text" class="form-control" v-model="manufacturer" id="manufacturer" />
      </div>
      <div class="form-group">
        <label for="description">Description</label>
        <input type="text" class="form-control" v-model="description" id="description" />
      </div>
      <div class="form-group">
        <label for="price">Price</label>
        <input
          type="text"
          class="form-control"
          v-model="price"
          id="price"
        />
      </div>
      <div class="form-group">
        <label for="quantity">Quantity</label>
        <input
          type="text"
          class="form-control"
          v-model="quantity"
          id="quantity"
        />
      </div>

      <button type="submit" class="btn btn-primary mt-4">Add</button>
    </form>
  </div>

  <form></form>
</template>

<script>
export default {
  data() {
    return {
      item: "",
      manufacturer: "",
      description: null,
      price: null,
      quantity: null,
    };
  },
  methods: {
    postData(e) {
      e.preventDefault();

      const postData = {
        item: this.item,
        manufacturer: this.manufacturer,
        description: this.description,
        price: this.price,
        quantity: this.quantity,
      };
      console.log(postData);

      fetch("http://127.0.0.1:8000/api/computer-items/store", {
        method: "POST",
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json",
        },
        body: JSON.stringify(postData),
      })
        .then((response) => {
          if (response.status === 200) {
            this.$router.push({ path: "/computer-items" });
          }
        })
        .catch((err) => console.log(err));
    },
    mounted() {
      this.postData();
    },
  },
};
</script>

<style></style>
