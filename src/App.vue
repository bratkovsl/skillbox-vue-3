<template>
  <div>
    <header class="header">
      <div class="header__wrapper container">
        <span class="header__info">Каталог</span>

        <a class="header__logo" href="#">
          <img src="img/svg/logo-tech.svg" alt="Логотип интернет магазина Технозавррр"
               width="190"
               height="33">
        </a>

        <a class="header__tel" href="tel:8 800 600 90 09">
          8 800 600 90 09
        </a>
        <CardIndicator />
      </div>
    </header>
    <router-view/>
    <footer class="footer">
      <div class="footer__wrapper container">
        <ul class="footer__links">
          <li>
            <a class="footer__link" href="#">
              Каталог
            </a>
          </li>
          <li>
            <a class="footer__link" href="tel:88006009009">
              8 800 600 90 09
            </a>
          </li>
          <li>
            <a class="footer__link" href="mailto:hi@technozavrrr.com">
              hi@technozavrrr.com
            </a>
          </li>
          <li>
            <a class="footer__link" href="#">
              Распродажа
            </a>
          </li>
          <li>
            <a class="footer__link footer__link--medium" href="#">
              Заказать звонок
            </a>
          </li>
        </ul>

        <ul class="footer__social social">
          <li class="social__item">
            <a class="social__link" href="#" aria-label="Вконтакте">
              <svg width="20" height="11" fill="currentColor">
                <use xlink:href="#icon-vk"></use>
              </svg>
            </a>
          </li>
          <li class="social__item">
            <a class="social__link" href="#" aria-label="Инстаграм">
              <svg width="17" height="17" fill="currentColor">
                <use xlink:href="#icon-insta"></use>
              </svg>
            </a>
          </li>
          <li class="social__item">
            <a class="social__link" href="#" aria-label="Facebook">
              <svg width="17" height="17" fill="currentColor">
                <use xlink:href="#icon-facebook"></use>
              </svg>
            </a>
          </li>
          <li class="social__item">
            <a class="social__link" href="#" aria-label="Twitter">
              <svg width="17" height="14" fill="currentColor">
                <use xlink:href="#icon-twitter"></use>
              </svg>
            </a>
          </li>
          <li class="social__item">
            <a class="social__link" href="#" aria-label="Telegram">
              <svg width="19" height="17" fill="currentColor">
                <use xlink:href="#icon-telegram"></use>
              </svg>
            </a>
          </li>
        </ul>

        <p class="footer__desc">
          Все права на материалы, находящиеся на сайте, охраняются в соответствии с
          законодательством РФ,
          в том числе об авторском праве и смежных правах.
        </p>

        <ul class="footer__data">
          <li>
            <a class="footer__link" href="#" target="_blank" rel="noopener" type="application/pdf">
              Политика конфиденциальности
            </a>
          </li>
          <li>
            <a class="footer__link" href="#" target="_blank" rel="noopener" type="application/pdf">
              Публичная оферта
            </a>
          </li>
        </ul>

        <span class="footer__copyright">
          © 2020 Технозавррр
        </span>
      </div>
    </footer>
  </div>
</template>

<script>
import CardIndicator from '@/components/CardIndicator.vue';
import { mapActions, mapMutations } from 'vuex';

export default {
  components: { CardIndicator },
  created() {
    const userAccessKey = localStorage.getItem('userAccessKey');
    if (userAccessKey) {
      this.updateUserAccessKey(userAccessKey);
    }
    this.loadCart();
  },
  methods: {
    ...mapActions(['loadCart']),
    ...mapMutations(['updateUserAccessKey']),
  },
};
</script>
