<template>
   <nav class="navbar navbar-light fixed-top">
            <div class="navbar-text ml-auto d-flex">
                <buttton class="btn btn-sm btn-outline-success" @click="$emit('toogle')">
                    <font-awesome-icon icon="dollar-sign"></font-awesome-icon>
                </buttton>
                <div class="dropdown ml-2" v-if="cart.length > 0">
                    <button class="btn btn-success btn-sm dropdown-toggle" id="dropdownCart123" data-toggle="dropdown"
                        aria-haspopup="true" aria-expanded="false">
                        <span class="badge badge-pill badge-light">{{ cartQty }}</span>
                        <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
                        {{ cartTotal | currencyFormat }}
                    </button>
                    <div class="dropdown-menu dropdown-menu-right" aria-labelledby="dropdownCart">
                        <div v-for="(item, index) in cart" :key="index">
                            <div class="dropdown-item-text text-nowrap text-right">
                                <span class="badge badge-pill badge-warning align-text-top mr-1">
                                    {{ item.qty }}
                                </span>
                                {{ item.product.name }}
                                <b>{{ item.qty * item.product.price | currencyFormat }}</b>
                                <a href="#" class="badge badge-danger text-white" @click.stop="$emit('delete', index)">-</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </nav>

</template>

<script>
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
import Price from "./Price.vue";

export default {
    name: "navbar",
    components: {
        FontAwesomeIcon,
        Price
    },
    props: ["cart", "cartQty", "cartTotal"],
    filters: {
    currencyFormat: function (value) {
      return "$" + Number.parseFloat(value).toFixed(2);
    }
  },
}
</script>