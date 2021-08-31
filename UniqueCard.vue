<template>
    <div class="pop_wrapper" ref="pop_wrapper">
        <div class="v-popup">
        <div class="v-popup__header">
            <span></span>
            <span>
                <i 
                    style="cursor:pointer"
                    class="material-icons"
                    @click="colsePopup"
                >
                    close
                </i>
            </span>
        </div>
        <div class="v-popup__content">
            <slot></slot>
        </div>
        <div class="v-popup__footer">
            <button 
                @click="colsePopup"
                class="close_modal"
            >
            Close
            </button>
            <button class="submit_btn">В корзину</button>
        </div>
        
    </div>
    </div>
</template>

<script>
    export default {
        props: {
            pizzaCard: {
                type: Array,
                required: true
            }
        },
        methods: {
            colsePopup() {
                this.$emit('closePopup');
            },
            mounted() {
                let vm = this;
                document.addEventListener('click', function(item) {
                    if (item.target === vm.$refs['pop_wrapper']) {
                        this.colsePopup();
                    }
                });
            }
        }  
    }
</script>

<style>
.pop_wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0; 
    right: 0;
    left: 0;
    bottom: 0;
    background-color: rgb(35, 35, 35, 0.4);
}
.v-popup {
    padding: 16px;
    left: calc(50% - 225px);
    position: fixed;
    top: 50px;
    width: 400px;
    background: #fff;
    box-shadow: 4px 4px 4px rgb(35, 35, 35, 0.2);
    border-radius: 10px;
    border: 1px solid rgb(35, 35, 35, 0.2);
}
.v-popup__header, .v-popup__footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.v-popup__content {
        display: grid;
        justify-content: center;
        align-items: center;
        gap: 1em;
    }
    .submit_btn {
        width: 8em;
        padding: 8px;
        color: #fff;
        background:#ffcd819c;
        border-radius: 5px;
    }
    .submit_btn:hover {
        border-color: #ffcc81;
        width: 8em;
        padding: 8px;
        color: #fff;
        border-radius: 5px;
    }
    .close_modal {
        padding: 8px;
        color: #fff;
        background: rgb(35, 35, 35, 0.2);
        border-radius: 5px;
    }
    
</style>