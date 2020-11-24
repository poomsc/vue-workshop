<template>
  <div id="app">
    <div class="container">
      <h2 align="center">Workshop #3 - คำนวนราคา</h2>
      <hr />
      <div class="row">
        <div class="col-md-2" v-for="product in products" :key="product.name">
          <div class="card h-100">
            <img
              :src="product.image"
              alt="product.name"
              class="rounded card-img-top"
            />
            <div class="card-body">
              <h4 class="card-title">{{ product.name }}</h4>
              <p class="card-text">Price {{ product.price }} ฿</p>
            </div>
            <div class="card-footer">
              <button class="btn-primary btn" v-on:click="addToCart(product)">
                add to cart
              </button>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <table class="table table-hover">
            <thead>
              <tr>
                <th scope="col">pic</th>
                <th scope="col">name</th>
                <th scope="col"></th>
                <th scope="col">price</th>
                <th scope="col">amout</th>
                <th scope="col">total</th>
                <th scope="col">remove</th>
              </tr>
            </thead>
            <tbody v-for="product in products" :key="product.name">

              <tr v-if="product.amount > 0">
                <th scope="row">
                  <img
                    :src="product.image"
                    alt="product.name"
                    class="rounded card-img-top"
                  />
                </th>
                <td colspan="2" class="text-left">{{ product.name }}</td>
                <td>{{ product.price }}</td>
                <td>{{ product.amount }}</td>
                <td>{{ product.amount * product.price }}</td>
                <td>
                  <button
                    class="btn-danger btn btn-sm"
                    @click="removeFromCart(product)"
                  >
                    x
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
          <div class="my-5">
            <h4 align="center">Total price {{ total() }}</h4>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: [
        {
          id: 1,
          name: "กาแฟเย็น",
          price: 30,
          image:
            "https://www.nestleprofessional.co.th/sites/g/files/gfb531/f/styles/recipe/public/media/nescafe-iced-signature-540x400.jpg",
          amount: 0,
        },
        {
          id: 2,
          name: "ชาเย็น",
          price: 40,
          image:
            "https://kcinterfoods.co.th/upload-img/Meow_/product_cover/Thaimilkteamix_7.png",
          amount: 0,
        },
        {
          id: 3,
          name: "ชาเขียนว",
          price: 50,
          image:
            "https://kcinterfoods.co.th/upload-img/Meow_/product_cover/MatchaB_10.png",
          amount: 0,
        },
        {
          id: 4,
          name: "นมสด",
          price: 60,
          image: "https://gf.lnwfile.com/eu1pip.jpg",
          amount: 0,
        },
      ],
    };
  },
  methods: {
    addToCart: function(product) {
      product.amount++;
    },
    removeFromCart: function(product) {
      product.amount = 0;
    },
    total: function() {
      var sum = 0;
      this.products.forEach((product) => {
        sum += product.price * product.amount;
      });
      return sum;
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
</style>
