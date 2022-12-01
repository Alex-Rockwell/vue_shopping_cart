<template>
  <section class="v-productlist">
    <h2 class="v-productlist__title">Просмотренные товары</h2>
    <swiper
      :slidesPerView="4"
      :spaceBetween="10"
      :slidesPerGroup="4"
      :loop="true"
      :pagination="{
        type: 'fraction',
      }"
      :navigation="true"
      :modules="[Pagination, Navigation]"
      class="mySwiper"
    >
      <swiper-slide v-for="product in viewedProducts" :key="product.id">
        <ViewedProductsItem :product="product" />
      </swiper-slide>
    </swiper>
  </section>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
import "swiper/css/navigation";
import { Pagination, Navigation } from "swiper";

import ViewedProductsItem from "./ViewedProductsItem.vue";
import { storeToRefs } from "pinia";
import { useViewedProductsStore } from "../stores/viewedProductsStore";

const productsStore = useViewedProductsStore();
const { viewedProducts } = storeToRefs(productsStore);
console.log(viewedProducts.value);
</script>

<style lang="scss" scoped>
.swiper {
  width: 100%;
  height: 100%;
}

.swiper-slide {
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}

.v-productlist__title {
  font-weight: 600;
  font-size: 30px;
  line-height: 1.2;
}
</style>
