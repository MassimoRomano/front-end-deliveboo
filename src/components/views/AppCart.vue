<script>
import { store } from '../store.js';
export default {
    name: 'AppCart',
    data() {
        return {
            store,
        };
    },
    methods: {
        goToRestaurant() {
            const restaurantSlug = JSON.parse(localStorage.getItem("old_slug"));
            if (restaurantSlug) {
                this.$router.push({ name: 'restaurant', params: { slug: restaurantSlug } });

            }
        }
    },
};

</script>


<template>
    <div class="app-carrello">
        <div class="carrello-wrapper" @click="this.goToRestaurant()">
            <!-- Icona del carrello -->
            <i class="carrello-icon fa-solid fa-cart-shopping"></i>
            <!-- Nuvoletta con la quantità nel carrello -->
            <span class="carrello-quantity">{{ store.Cart.items }}</span>
        </div>
        <!-- Aggiungi qui il contenuto del carrello -->
    </div>
</template>

<style>
.app-carrello {
    position: fixed;
    top: 100px;
    right: 20px;
    z-index: 100;
    /* Assicura che il carrello sia sopra gli altri elementi */
}

.carrello-wrapper {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 50px;
    height: 50px;
    background-color: var(--deliverboo-eighty);
    border-radius: 50%;
    cursor: pointer;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s ease;
}

.carrello-wrapper:hover {
    background-color: var(--deliverboo-eighty);

}

.carrello-icon {
    font-size: 24px;
    color: white;
}

.carrello-quantity {
    width: 25px;
    height: 25px;
    position: absolute;
    top: -10px;
    right: -10px;
    background-color: red;
    color: white;
    border-radius: 50%;
    padding: 2px 6px;
    font-size: 14px;
    font-weight: bold;
    display: flex;
    align-items: center;
    justify-content: center;

}
</style>
