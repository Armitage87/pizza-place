<template>
  <div class="row">
    <div class="col-sm-12 col-md-6">
      <table class="table table-hover">
        <thead class="thead-default">
          <tr>
            <th>Size</th>
            <th>Price</th>
            <th>Add to Basket</th>
          </tr>
        </thead>
        <tbody v-for="item in getMenuItems" :key="item.name">
          <tr>
            <td>
              <strong>{{ item.name }}</strong>
            </td>
          </tr>
          <tr v-for="option in item.options" :key="option.key">
            <td>{{ option.size }}</td>
            <td>{{ option.price }}</td>
            <td>
              <button
                class="btn btn-sm btn-outline-success"
                type="button"
                @click="addToBasket(item, option)"
              >
                +
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="col-sm-12 col-md-6">
      <div v-if="basket.length > 0">
        <table class="table">
          <thead class="thead-default">
            <tr>
              <th>Quantity</th>
              <th>Item</th>
              <th>Total</th>
            </tr>
          </thead>
          <tbody v-for="item in basket" :key="item.indexOf">
            <tr>
              <td>
                <button class="btn btn-sm" type="button" @click="decreaseQuantity(item)">-</button>
                <span>{{ item.quantity }}</span>
                <button class="btn btn-sm" type="button" @click="increaseQuantity(item)">+</button>
              </td>
              <td>{{ item.name }} {{ item.size }}</td>
              <td>{{ item.price * item.quantity }}</td>
            </tr>
          </tbody>
        </table>
        <p>Order total:</p>
        <button class="btn btn-success btn-block">Place Order</button>
      </div>
      <div v-else>
        <p>{{ basketText }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      basket: [],
      basketText: "Tout basket is empty!",
      getMenuItems: {
        1: {
          name: "Margherita",
          description: "A delicious tomato based pizza topped with mozzarella",
          options: [
            {
              key: 1,
              size: 9,
              price: 6.95
            },
            {
              key: 2,
              size: 12,
              price: 10.95
            }
          ]
        },
        2: {
          name: "Pepperoni",
          description:
            "A delicious tomato based pizza topped with mozzarella and pepperoni",
          options: [
            {
              key: 1,
              size: 9,
              price: 7.95
            },
            {
              key: 2,
              size: 12,
              price: 12.95
            }
          ]
        },
        3: {
          name: "Ham and Pineapple",
          description:
            "A delicious tomato based pizza topped with mozzarella, ham and pineapple",
          options: [
            {
              key: 1,
              size: 9,
              price: 7.95
            },
            {
              key: 2,
              size: 12,
              price: 12.95
            }
          ]
        }
      }
    };
  },
  methods: {
    addToBasket(item, option) {
      this.basket.push({
        name: item.name,
        price: option.price,
        size: option.size,
        quantity: 1
      });
    },
    removeFromBasket(item) {
        this.basket.splice(this.basket.indexOf(item), 1);
    },
    increaseQuantity(item) {
        item.quantity++;
    },
    decreaseQuantity(item) {
        item.quantity--;
        if(item.quantity === 0) {
            this.removeFromBasket(item);
        }
    }
  }
};
</script>
