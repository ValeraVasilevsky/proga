<template>
    <div style="textAlign:center">
        <div class="title">
            <h2 id="Pizza">Pizza</h2>
        </div>
        <div class="wrapper">
            <div class="card"
                v-for="item in pizza"
                :key="item"
            >
                <unique-card     
                    v-if="isInfoPopupVisible"
                    @closePopup='colseInfoPopup'
                >
                    <img class="cardImg" :src="item.image" alt="">
                    <div>
                        <h3>{{item.title}}</h3>
                        <p>{{item.body}}</p>
                    </div>
                </unique-card>

                <img
                    @click="showPopupInfo" 
                    class="cardImg" 
                    :src="item.image" 
                    alt="pizza"
                >
                <h2>{{item.title}}</h2>
                <div class="card-body">
                    <p>{{item.body}}</p>

                    <div class="btns"
                        v-if="item.counter === 0"
                        style="display:flex;justifyContent:center;alignItems:center"
                    >
                        <button class="button">{{item.price}}</button>
                        <button 
                            @click="item.counter++"
                            id="to-cart"
                            class="button"
                        >
                        {{item.btnToCart}}
                        </button>
                    </div>

                    <div class="btns"
                        v-else
                        style="display:flex;justifyContent:center;gap:1em"
                    >
                        <button class="button">{{item.price}}</button>
                        <button
                            @click="item.counter++" 
                            class="button"
                            id="to-cart">
                            {{item.btnToCart}}: {{item.counter}}
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <div class="title">
            <h2 id="Rolls">Rolls</h2>
        </div>
        <div class="wrapper">
            <div class="card"
                v-for="item in rolls"
                :key="item"
            >
                

                <unique-card 
                    :pizzaCard="item"
                    v-if="isInfoPopupVisible"
                    @closePopup='colseInfoPopup'
                >
                    <img class="cardImg" :src="item.image" alt="">
                    <div>
                        <h3>{{item.title}}</h3>
                        <p>{{item.body}}</p>
                    </div>
                </unique-card>

                <img @click="showPopupInfo" class="cardImg" :src="item.image" alt="pizza">
                <h2>{{item.title}}</h2>
                <div class="card-body">
                    <p>{{item.body}}</p>

                    <div class="btns"
                        v-if="item.counter === 0"
                        style="display:flex;justifyContent:center;alignItems:center"
                    >
                        <button class="button">{{item.price}}</button>
                        <button 
                            @click="item.btnToCart = 'Добавлено'"
                            id="to-cart"
                            class="button"
                        >
                        {{item.btnToCart}}
                        </button>
                    </div>

                    <div class="btns"
                        @click="item.btnToCart = 'Добавлено'"
                        v-else
                        style="display:flex;justifyContent:center;gap:1em"
                    >
                        <button class="button">{{item.price}}</button>
                        <button 
                            class="button"
                            id="to-cart">
                            {{item.btnToCart}}: {{item.counter}}
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <div class="title">
            <h2 id="WOK">WOK</h2>
        </div>
        <div class="wrapper">
            <div class="card"
                v-for="item in wok"
                :key="item"
            >

                <unique-card 
                    
                    v-if="isInfoPopupVisible"
                    @closePopup='colseInfoPopup'
                >
                    <img class="cardImg" :src="item.image" alt="">
                    <div>
                        <h3>{{item.title}}</h3>
                        <p>{{item.body}}</p>
                    </div>
                </unique-card>

                <img @click="showPopupInfo" class="cardImg" :src="item.image" alt="pizza">
                <h2>{{item.title}}</h2>
                <div class="card-body">
                    <p>{{item.body}}</p>

                    <div class="btns"
                        v-if="item.counter === 0"
                        style="display:flex;justifyContent:center;alignItems:center"
                    >
                        <button class="button">{{item.price}}</button>
                        <button 
                            @click="item.btnToCart = 'Добавлено'"
                            id="to-cart"
                            class="button"
                        >
                        {{item.btnToCart}}
                        </button>
                    </div>

                    <div class="btns"
                        @click="item.btnToCart = 'Добавлено'"
                        v-else
                        style="display:flex;justifyContent:center;gap:1em"
                    >
                        <button class="button">{{item.price}}</button>
                        <button 
                            class="button"
                            id="to-cart">
                            {{item.btnToCart}}: {{item.counter}}
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <div class="title">
            <h2 id="">Drinks</h2>
        </div>
        <div class="wrapper">
            <div class="card"
                v-for="item in drinks"
                :key="item"
            >

                <unique-card 
                    
                    v-if="isInfoPopupVisible"
                    @closePopup='colseInfoPopup'
                >
                    <img class="cardImg" :src="item.image" alt="">
                    <div>
                        <h3>{{item.title}}</h3>
                        <p>{{item.body}}</p>
                    </div>
                </unique-card>

                <img @click="showPopupInfo" class="cardImg" :src="item.image" alt="pizza">
                <h2>{{item.title}}</h2>
                <div class="card-body">
                    <p>{{item.body}}</p>

                    <div class="btns"
                        v-if="item.counter === 0"
                        style="display:flex;justifyContent:center;alignItems:center"
                    >
                        <button class="button">{{item.price}}</button>
                        <button 
                            @click="item.btnToCart = 'Добавлено'"
                            id="to-cart"
                            class="button"
                        >
                        {{item.btnToCart}}
                        </button>
                    </div>

                    <div class="btns"
                        @click="item.btnToCart = 'Добавлено'"
                        v-else
                        style="display:flex;justifyContent:center;gap:1em"
                    >
                        <button class="button">{{item.price}}</button>
                        <button 
                            class="button"
                            id="to-cart">
                            {{item.btnToCart}}: {{item.counter}}
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import UniqueCard from './UniqueCard.vue'

    export default {
        components: {
            'UniqueCard': UniqueCard
        },
        data() {
            return {
                isInfoPopupVisible: false
            }
        },
        props: {
            pizza: {
                type: Array,
                required: true
            },
            rolls: {
                type: Array,
                required: true
            },
            wok: {
                type: Array,
                required: true
            },
            drinks: {
                type: Array,
                required: true
            }
        },
        methods: {
            showPopupInfo() {
                this.isInfoPopupVisible = true
            },
            colseInfoPopup() {
                this.isInfoPopupVisible = false
            },
            addprod() {}
        }
        
    }
</script>

<style>
  * {
    padding: 0;
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    scroll-behavior: smooth;
    color: rgb(35, 35, 35);
  }
  
  .cardPage {
    display: none;
  }

  #delivery {
    display: block;
  }
  .wrapper {
    display: grid;
    grid-template-columns: 20% 20% 20% 20% 20%;
    place-items: center;
    margin-top: 1em;
    margin-bottom: 1em;
  }
  .title {
      height: 2em;
      display: grid;
      place-items: center;
  }
  .wrapper > div {
    height: auto;
    padding: 0.5em;
    display: grid;
    place-items: center;
  }
  .button {
      margin: 1em;
      display: block;
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
    border-radius: 5px;
    width: 7em;
    height: 2.5em;
  }
  #to-cart:hover {
    background-color: #ffcc81;
    border-radius: 5px;
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
    height: 30rem;
    border-radius: 15px;
    border: 1px solid rgb(35, 35, 35, 0.2);
    gap: 1em;
    transition: all ease-in-out 0.3s;
    width: 15em;
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
  .cardImg {
      width: 200px;
      height: 200px;
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