<template>
  <div class="article-block">
    <Article v-if="!showValue" v-for="(article, index) in articles" :key="index" :articleData="article"
      v-on:show-full-article="showFullArticle" />
    <ArticleFull v-for="(article, index) in articleOne" :key="index" :articleData="article"
      v-on:hide-full-article="hideFullArticle" v-if="showValue" />
  </div>
</template>

<script>

import Article from './Article.vue';
import ArticleFull from './ArticleFull.vue';

export default {
  components: {
    Article,
    ArticleFull,
  },
  data() {
    return {
      showValue: false,
      articles: [
        {
          id: 0,
          title: "Сучасні тенденції у веб-розробці на JavaScript",
          anons: "Огляд найновіших технологій та інструментів у веб-розробці на JavaScript.",
          full_text: `Продовжуємо використовувати HTML, CSS та JavaScript
HTML, CSS та JavaScript є основою веб- розробки і їх використання буде продовжуватись у 2023 році.HTML є мовою розмітки, CSS — мовою стилізації, а JavaScript — мовою програмування, яка дозволяє додавати динамічність до веб - сторінок.Проте, для виконання більш складних завдань, можна використовувати бібліотеки та фреймворки.`,
          img: "https://denzadnem.com.ua/wp-content/uploads/2023/04/veb-rozrobka.jpg"
        },
        {
          id: 1,
          title: "Розробка інтерфейсів за допомогою React.js",
          anons: "Вивчення основ та найкращих практик розробки інтерфейсів з використанням бібліотеки React.js.",
          full_text: "React розробник це фахівець, який відіграє ключову роль у створенні веб-додатків з використанням цієї бібліотеки. Він відповідає за розробку компонентів, управління станом і обробку подій користувацького інтерфейсу. Розробник React повинен мати глибоке розуміння JavaScript, а також розуміти основи HTML і CSS. Він повинен уміти розбивати користувацький інтерфейс на маленькі компоненти, які можна використовувати повторно, і керувати станом програми.",
          img: "https://cdn-ckkcn.nitrocdn.com/zFBNvlNnhjnAtIruckhWUtdrrYcfdzYJ/assets/images/optimized/rev-1e99984/foxminded.ua/wp-content/uploads/2023/06/backend-razrabotchik-1366x768.jpg"
        },
        {
          id: 2,
          title: "Робота з асинхронністю в JavaScript",
          anons: "Навчання ефективного використання асинхронних функцій та обіцянок для оптимізації роботи програм на JavaScript.",
          full_text: `Метою вивчення навчальної дисципліни «Асинхронне програмування у веб» є набуття здобувачами вищої освіти спеціальних знань та практичних навичок з питань створення додатків для глобальної мережі Інтернет з використанням асинхронного програмування для оптимізації високонавантажених програм із частим очікуванням системи.

            Основними завданнями вивчення дисципліни «Асинхронне програмування у веб» є:

–  засвоєння особливостей розробки веб- додатків;

–  оволодіння загальними поняттями синхронного та асинхронного програмування;

–  оволодіння знаннями з концепції та прикладів асинхронного програмування;

–  засвоєння основних технологічних методів практичного застосування асинхронного програмування для розробки програмного продукту.`,
          img: "https://img.devzone.org.ua/800x,jpeg/https://ig.devzone.org.ua/api/og?url=https://devzone.org.ua/post/osnovi-asinxronnogo-programuvannia-na-javascript"
        },
        {
          id: 3,
          title: "Огляд фреймворку Vue.js",
          anons: "Детальне вивчення Vue.js - легкого та гнучкого фреймворку для розробки інтерфейсів.",
          full_text: "Ви коли-небудь замислювалися, як створювати інтерактивні та елегантні користувацькі інтерфейси для ваших веб-додатків? Можливо, вам хотілося б мати потужний інструмент, який спрощує розробку фронтенду і забезпечує гладку роботу ваших додатків. І ось тут на сцену виходить Vue.js – це сучасний JavaScript-фреймворк для розробки користувацьких інтерфейсів. Він надає зручні інструменти та можливості для створення інтерактивних веб-додатків. Однією з його головних переваг є легковажність і простота у використанні (навіть новачки в розробці веб-додатків швидко освоюють його основи завдяки інтуїтивному синтаксису і простому API). Водночас він має достатній функціонал для розробки складних проектів.",
          img: "https://mobiosolutions.com/wp-content/uploads/2019/10/What-is-Vue.js-advantages-and-disadvantages.png"
        },
        {
          id: 4,
          title: "GraphQL: Сучасний підхід до роботи з API",
          anons: "Огляд технології GraphQL, яка надає ефективний і гнучкий інтерфейс для взаємодії з сервером.",
          full_text: "GraphQL — сервіс, який створений за допомогою описання типів та їх полів. Іншими словами — це один з підходів організації інтерфейсу взаємодії між клієнтом та сервером. У статті говоримо про API розробку за допомогою GraphQL на платформі .NET, різницю між GraphQL та REST, розглянемо основні компоненти GraphQL, «за» та «проти» його використання.",
          img: "https://img.devzone.org.ua/800x,jpeg/https://devzone.org.ua/storage/posts/2020/10/5f7f2b17b3752.webp"
        },
        {
          id: 5,
          title: "Тестування веб-додатків на JavaScript з використанням Jest",
          anons: "Прийоми та стратегії для ефективного тестування веб-додатків на JavaScript з використанням фреймворку Jest.",
          full_text: `Тестування є невід'ємною частиною розробки програмного забезпечення, яка допомагає виявити та усунути помилки та недоліки у вашому коді.

У веб - розробці тестування JavaScript - коду вкрай важливе, оскільки веб - додатки взаємодіють з різноманітними браузерами та пристроями.У цій статті я пропоную детально розглянути, що можна робити за допомогою JavaScript для тестування коду та подивитися приклади різних підходів та інструментів для створення тестів.`,
          img: "https://assets.ithillel.ua/images/blog/cover/_transform_blogSplash_desktop_2x/Blog-JsTesting.jpg"
        }
      ],
      articleOne: [],
    }
  },
  methods: {
    showFullArticle(showValue, id) {
      this.showValue = showValue;
      this.articleOne = this.articles.filter(article => article.id == id);
    },
    hideFullArticle(showValue) {
      this.showValue = showValue;
    }
  }
}
</script>

<style>
.article-block {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
</style>