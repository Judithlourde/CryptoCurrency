<template>
    <main class="main">
        <div>CRYPTO</div>
        <div>PRICE</div>
        <div>MARKED CAP</div>
        <div>24H</div>
    </main>

    <hr class="seperator">
    
    <div> 
    <ul class="" v-for="value in cryptoArray" :key="value.rank">
        <div class="main__list">
            <div>
                <li>{{ value.name }}</li>
                <li>{{ value.symbol }}</li>
            </div>
            
            <li>$ {{ value.priceUsd.substring(0, 8) }}</li>
            <li>$ {{ value.marketCapUsd.substring(0, 3) }} Billion</li>
            <li v-if="value.changePercent24Hr.charAt(0) === `-`"><img src="/images/svg/down-arrow.svg" alt=""></li>
            <li v-else><img src="/images/svg/up-arrow.svg" alt=""></li>
        </div>
        
        <hr class="seperator">
    </ul>
    
    </div>
    
</template>

<script>
    export default {
        data() {
            return {
                cryptoArray: [],
            }
        },

        created() {
            this.fetchData();
            console.log(this.changePercent);
           
        },

        methods: {
            async fetchData() {
                const cryptoUrl = 'https://api.coincap.io/v2/assets';
                const response = await fetch(cryptoUrl);
                const {data}  = await response.json(); 

                const value = data.filter(crypto => crypto.symbol === 'BTC' || crypto.symbol === 'ETH' || crypto.symbol === 'USDT' || crypto.symbol === 'BNB' || crypto.symbol === 'HEX' || crypto.symbol === 'USDC');
                this.cryptoArray = value;  
                console.log(value);

            },
        },
    }
</script>

<style>
    .main,
    .main__list {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        text-align: center;
        margin: 20px 0;
    }

    .main__list {
        list-style: none;
    }

    .seperator {
		opacity: 0.33;
		border-style: solid;
		border-bottom-width: 1px;
		border-top-width: 0;
		border-left-width: 0;
    	margin: 1% 10%;
	}
</style>