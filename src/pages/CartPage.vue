<template>
  <main class="content container">
    <div class="content__top">
      <ul class="breadcrumbs">
        <li class="breadcrumbs__item">
          <router-link class="breadcrumbs__link" :to="{name: 'main'}">
            Каталог
          </router-link>
        </li>
        <li class="breadcrumbs__item">
          <a class="breadcrumbs__link">
            Корзина
          </a>
        </li>
      </ul>

      <h1 class="content__title">
        Корзина
      </h1>
      <span class="content__info">
<!--        eslint-disable-next-line -->
        {{ productCounter }} {{ numWord(productCounter, ['товар', 'товара', 'товаров']) }}
      </span>
    </div>
    <section class="cart">
      <BaseLoader v-if="$store.state.cartSpinner"/>
      <form v-else class="cart__form form" action="#" method="POST">
        <div class="cart__field">
          <ul class="cart__list">
            <CartItem :item="item" v-for="item in products" :key="item.productId"/>
          </ul>
        </div>

        <div class="cart__block">
          <p class="cart__desc">
            Мы посчитаем стоимость доставки на следующем этапе
          </p>
          <p class="cart__price">
            Итого: <span>{{ totalPrice | numberFormat }} ₽</span>
          </p>

          <router-link tag="button" :to="{name:'order'}" :disabled="productCounter===0"
                       class="cart__button button button--primery"
                       type="submit">
            Оформить заказ
          </router-link>
        </div>
      </form>
    </section>
  </main>
</template>

<script>
import numberFormat from '@/helpers/numberFormat';
import numWord from '@/helpers/numWord';
import { mapGetters } from 'vuex';
import CartItem from '@/components/CartItem.vue';
import BaseLoader from '@/components/BaseLoader.vue';

export default {
  components: {
    BaseLoader,
    CartItem,
  },
  data() {
    return {
      numWord,
    };
  },
  filters: {
    numberFormat,
  },
  computed: {
    ...mapGetters({
      products: 'cartDetailProducts',
      totalPrice: 'cartTotalPrice',
      productCounter: 'cartProductAmount',
    }),
  },
};
</script>
