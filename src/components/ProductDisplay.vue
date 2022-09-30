<script>
export default {
  props: {
    premium: {
      type: Boolean,
      required: true,
    },
  },

  data() {
    return {
      selectedVariant: 0,
      onSale: false,
      details: ["50% premium coton", "50% nature whole"],

      variants: [
        {
          id: 1,
          color: "brown",
          image: "/src/assets/img/red-tshirt.png",
          tag: ["sport", "fitness", "trendy"],
          brand: "Adidas",
          category: "Sport",
          product: "t-shirt",
          quantity: 1,
          price: 10,
          description:
            "The New Short Sleeve Garment-Dyed Vintage T-Shirt (No. 6337). Garment-dyed 100% cotton slub. One chest pocket (always handy). Noticeably more substantial cotton than you normally find in T-shirts these days, garment-dyed to achieve the effect of great age. Although newborn, they start out looking good (and old).",
        },
        {
          id: 2,
          color: "blue",
          image: "/src/assets/img/blue-tshirt.png",
          brand: "Nike",
          category: "Sport",
          product: "t-shirt",
          tag: ["sport", "fitness", "trendy"],
          quantity: 0,
          price: 12,
          description:
            "The Great New Short Sleeve Garment-Dyed Vintage T-Shirt (No. 6607). Garment-dyed 100% cotton slub. One chest pocket (always handy). Noticeably more substantial cotton, garment-dyed to achieve the effect of great age. Although newborn, they start out looking good (and old).",
        },
        {
          id: 3,
          color: "purple",
          image: "/src/assets/img/purple-tshirt.png",
          tag: ["sport", "fitness", "trendy"],
          brand: "Nike",
          category: "Sport",
          product: "t-shirt",
          quantity: 50,
          price: 12,
          description:
            "Special New Short Sleeve Garment-Dyed Vintage T-Shirt (No. 64021). Garment-dyed 100% cotton slub. One chest pocket (always handy). Noticeably more substantial cotton than you normally find in T-shirts these days, garment-dyed to achieve the effect of great age.",
        },
      ],
      sizes: [36, 37, 39, 42, 44],
    };
  },

  computed: {
    titleProd() {
      return (
        this.variants[this.selectedVariant].category +
        " " +
        this.variants[this.selectedVariant].product
      );
    },
    currImg() {
      return this.variants[this.selectedVariant].image;
    },
    inStock() {
      if (this.variants[this.selectedVariant].quantity) return true;
      else return false;
    },
    displayPrice() {
      return this.variants[this.selectedVariant].price + "€";
    },
    displayCat() {
      return this.variants[this.selectedVariant].category.toLowerCase();
    },
    displayDescription() {
      return this.variants[this.selectedVariant].description;
    },
  },
  methods: {
    shipping() {
      if (this.premium) return "Free!";
      return "2.99";
    },
    updVariant(index) {
      return (this.selectedVariant = index);
    },
    addToCart() {
      let product = this.variants[this.selectedVariant];
      this.$emit("addToCartElem", this.inStock, product);
    },
  },
};
</script>

<template>
  <div class="product-container">
    <div class="row">
      <div class="col-md">
        <div class="">
          <div class="product-image">
            <img :src="currImg" class="tshirt" :class="{ hidden: !inStock }" />
          </div>
          <div class="product-info">
            <div class="title-price d-flex justify-content-between">
              <h1>{{ titleProd }}</h1>
              <div class="">
              <h4 class="fs-2">{{ displayPrice }}</h4>
            </div>
            </div>
            
            
            <div>
              <h3 v-if="inStock">in stock</h3>
              <h3 v-else>out of stock</h3>
            </div>
            <div>
              <span class="badge bg-warning text-dark">{{ displayCat }}</span>
            </div>
            <!-- prettier-ignore -->
            <div class="container-colors d-flex">

              <div v-for="(variant, index) in variants" :key="variant.id" @click="updVariant(index)">
                      <div class="circle-color mx-2" :style="{backgroundColor: variant.color != null ? variant.color: 'transparent'}"></div>
              </div>

            </div>
            <div>
              <p>{{ displayDescription }}</p>
            </div>
            <div class="">
              <!-- materials -->
              <div class="materials">
                <a
                  class="btn btn-secondary btn-sm"
                  data-bs-toggle="collapse"
                  href="#materialsMod"
                  role="button"
                  aria-expanded="false"
                  aria-controls="materialsMod"
                >
                  See materials
                </a>

                <div class="collapse ml-5" id="materialsMod">
                  <div class="card card-body">
                    <li v-for="detail in details" class="p-2">{{ detail }}</li>
                  </div>
                </div>
              </div>
            </div>
            <h3 v-show="onSale">On sale!</h3>

           
            <div class="shipping-container">
              <p>Shipping: {{ shipping() }}</p>
            </div>
            

            

            <select class="form-select" name="sizes" id="sizes">
              <option value="" disabled selected>Select size</option>
              <option v-for="size in sizes" :value="size">{{ size }}</option>
            </select>
            <div class="d-grid gap-2">
              <!-- add chart button -->
              <button
                class="add_cart btn btn-success mt-2"
                @click="addToCart"
              >
                Add to cart
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style></style>
