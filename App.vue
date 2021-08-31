<template>
  <div id="app">
    <div class="mainPage" id="Main">
      <mainhead></mainhead>
      <nav-main
        :categoryName="categoryName"
      ></nav-main>
      <cards class="cardPage" 
        id="cardsPage" 
        :pizza="pizza"
        :rolls="rolls"
        :wok="wok"
        :drinks="drinks"
      ></cards>
      <delivery style="display:none"></delivery>
      <footer-main></footer-main>
    </div>

  </div>
</template>

<script>
import Mainhead   from './components/Mainhead.vue'
import NavMain    from './components/NavMain.vue'
import Cards      from './components/Cards.vue'
import FooterMain from './components/FooterMain.vue'
import Delivery   from './components/Delivery.vue'
// import UniqueCard from './components/UniqueCard.vue'

export default {
  components: {
    'Mainhead'   : Mainhead,
    'NavMain'    : NavMain,
    'Cards'      : Cards,
    'FooterMain' : FooterMain,
    'Delivery'   : Delivery,
    // 'UniqueCard' : UniqueCard
  },
  data() 
  {
    return {
      categoryName:[
        { id: 1, name: 'Пицца', link: '#pizza'},
        { id: 2, name: 'Роллы', link: '#rolls'},
        { id: 3, name: 'WOK', link: '#wok'},
        { id: 4, name: 'Напитки', link: '#drinks'}
      ],
      pizza: [
        { id: 1, title: 'Миланская',      body: 'Описание 1', image: require('@/assets/unnamed.jpg'),   price: '$4', btnToCart: 'В корзину', counter: 0},
        { id: 2, title: 'Пепперони',      body: 'Описание 2', image: require('@/assets/pep.jpg'),       price: '$5', btnToCart: 'В корзину', counter: 0},
        { id: 3, title: 'Четыре Сыра',    body: 'Описание 3', image: require('@/assets/four.jpg'),      price: '$6', btnToCart: 'В корзину', counter: 0},
        { id: 4, title: 'Мексиксанская',  body: 'Описание 4', image: require('@/assets/mex.jpg'),       price: '$7', btnToCart: 'В корзину', counter: 0},
        { id: 5, title: 'Вегетарианская', body: 'Описание 5', image: require('@/assets/veg.jpg'),       price: '$3', btnToCart: 'В корзину', counter: 0},
      ],
      rolls: [
        { id: 1, title: 'Планета',        body: 'Описание 1', image: require('@/assets/one.jpg'),       price: '$4', btnToCart: 'В корзину', counter: 0, popup: ''},
        { id: 2, title: 'Роллы 1',        body: 'Описание 2', image: require('@/assets/fila.jpg'),      price: '$5', btnToCart: 'В корзину', counter: 0},
        { id: 3, title: 'Супер Лав',      body: 'Описание 3', image: require('@/assets/gul.jpg'),       price: '$6', btnToCart: 'В корзину', counter: 0},
        { id: 4, title: 'Гуливер',        body: 'Описание 4', image: require('@/assets/superLove.jpg'), price: '$7', btnToCart: 'В корзину', counter: 0},
        { id: 5, title: 'Филадельфия',    body: 'Описание 5', image: require('@/assets/planeta.jpg'),   price: '$3', btnToCart: 'В корзину', counter: 0}
      ],
      wok: [
        { id: 1, title: 'WOK 1',          body: 'Описание 1', image: require('@/assets/wok1.jpg'),     price: '$4', btnToCart: 'В корзину', counter: 0},
        { id: 2, title: 'WOK 2',          body: 'Описание 2', image: require('@/assets/wok2.jpg'),     price: '$5', btnToCart: 'В корзину', counter: 0},
        { id: 3, title: 'WOK 3',          body: 'Описание 3', image: require('@/assets/wok3.jpg'),     price: '$6', btnToCart: 'В корзину', counter: 0},
        { id: 4, title: 'WOK 4',          body: 'Описание 4', image: require('@/assets/wok4.jpg'),     price: '$7', btnToCart: 'В корзину', counter: 0},
        { id: 5, title: 'WOK 5',          body: 'Описание 5', image: require('@/assets/wok5.jpg'),     price: '$3', btnToCart: 'В корзину', counter: 0}
      ],
      drinks: [
        { id: 1, title: 'Name 1',         body: 'Описание 1', image: require('@/assets/d1.jpg'),       price: '$4', btnToCart: 'В корзину', counter: 0},
        { id: 2, title: 'Name 2',         body: 'Описание 2', image: require('@/assets/d2.jpg'),       price: '$5', btnToCart: 'В корзину', counter: 0},
        { id: 3, title: 'Name 3',         body: 'Описание 3', image: require('@/assets/d3.jpg'),       price: '$6', btnToCart: 'В корзину', counter: 0},
        { id: 4, title: 'Name 4',         body: 'Описание 4', image: require('@/assets/d4.jpg'),       price: '$7', btnToCart: 'В корзину', counter: 0},
        { id: 5, title: 'Name 5',         body: 'Описание 5', image: require('@/assets/d5.jpg'),       price: '$3', btnToCart: 'В корзину', counter: 0}
      ],
      allCards: [this.pizza, this.rolls, this.wok, this.drinks],
      isActive: false,
      isTrue: true,
      cartProd: []
    }
  },
  methods: {
    showPop() {
      
    },
    showInput() {
      let inputMain  = document.querySelector('.searchMain');

      inputMain.style.visibility = 'visible'
    },
    addClassToBtn() {
      let btnToCart = document.querySelector('#to-cart');

      btnToCart.addEventListener('mouseover', function() {
        if (this.isActive === false) {
          this.isActive = true;
        } else {
          this.isActive = false;
        }
      });
    },
    upCounter() {
      this.btnAddToCart = 'Добавлено:'
      this.counter++
    },
    addToCart() {
      let product = document.querySelectorAll('.card');

      product.forEach( function(item){
        this.cartProd.push(item);
        console.log(this.cartProd);
      });
    }
  }
}
</script>

<style>
  * {
    padding: 0;
    margin: 0;
    font-family:  Helvetica, Arial, sans-serif;
    scroll-behavior: smooth;
    color: rgb(35, 35, 35);
  }
  .cardPage {
    display: block;
  }
  #Delivery {
    display: none;
  }
  .wrapper {
    display: grid;
    grid-template-columns: 20% 20% 20% 20% 20%;
  }
  .wrapper > div {
    height: auto;
    padding: 0.5em;
    display: grid;
    place-items: center;
  }
  .onTop {
    width: 4em;
    height: 4em;
    background-color: rgba(164, 164, 164, 0.632);
    margin-left: 95%;
    margin-top: 36em;
    border-radius: 5px;
    position: fixed;
    opacity: 0.6;
  }
  .navigation {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .navigation > a {
    margin: 1em;
    text-decoration: none;
    outline: none;
    color: rgb(35, 35, 35);
    text-decoration: none;
    cursor: pointer;
    display: inline-block;
    font-size: 1.1em;
  }
  
  .iconArea {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .iconsFooter {
    padding-left: 1em;
  }
  #to-cart {
    background-color: #ffcd819c ;
    border-radius: 15px;
  }
  #to-cart:hover {
    background-color: #ffcc81;
    border-radius: 15px;
  }
  .icons {
    width: 24px;
    height: 24px;
    cursor: pointer;
  }
  .navigation > a::after {
    display: block;
    width: 0;
    height: 2px;
    background-color: #ffcc81;
    content: "";
    transition: width 0.3s ease-out;
  }
  .navigation > a:hover::after, .navigation > a:focus::after {
    width: 100%;
  }
  .links {
    color: #fff;
  }
  button {
    outline: none;
    border: none;
    background: none;
    cursor: pointer;
  }
  footer {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    width: auto;
    height: 5em;
    background-color: #ffcc81;
    background: rgb(243, 243, 243);
  }
  input {
    outline: none;
    background: none;
    border: none;
    width: 430px;
  }
  .header {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    width: auto;
    height: 4em;
    background-color: #ffcc81;
  }
  .box1 {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .box2 {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .box3 {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .box3 > .iconArea > img {
    margin: 15px;
  }
  .box2 > a {
    outline: none;
    color: rgb(35, 35, 35);
    margin: 1.2em;
    text-decoration: none;
    cursor: pointer;
    display: inline-block;
    font-size: 1.1em;
  }
  .box2 > a::after {
    display: block;
    width: 0;
    height: 1px;
    background-color: rgb(35, 35, 35);
    content: "";
    transition: width 0.3s ease-out;
  }
  .box2 > a:hover::after, .box2 > a:focus::after {
    width: 100%;
  }
  .card {
    display: grid;
    justify-content: center;
    align-items: center;
    background-color: #fff;
    height: 22rem;
    border-radius: 15px;
    border: 1px solid rgb(35, 35, 35, 0.2);
    gap: 1em;
    transition: all ease-in-out 0.3s;
  }
  .card:hover {
    box-shadow: 2px 2px 2px 2px rgb(35, 35, 35, 0.2);
    transition: all ease-in-out 0.2s;
  }
  .cards {
    width: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 5em;
    gap: 2.5em;
  }
  .card-body {
    display: grid;
    justify-content: center;
    align-items: center;
    gap: 2em;
    text-align: center;
  }
  .pizza {
    display: grid;
    grid-template-columns: 60% 40%;
    height: 100vh;
    width: auto;
  }
  .allCards {
    height: calc(100vh - 7em);
    display: grid;
    justify-content: center;
    align-items: center;
  }
  .searchMain {
    visibility: hidden;
    border: 1px solid rgb(35, 35, 35, 0.2);
    transition: all ease-in-out 0.2s;
    padding-left: 1em;
  }
  .searchMain:focus {
    border: 1px solid rgb(35, 35, 35);
    transition: all ease-in-out 0.2s;
  }
  .icons {
    transition: all ease-in-out 0.2s;
  }
  .icons:hover {
    transition: all ease-in-out 0.2s;
    transform: scale(1.1);
  }
</style>
