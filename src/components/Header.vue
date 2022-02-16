<template>
    <header class="header">
        <div class="header__logo">
            <img src="/images/svg/logo.svg" alt="money-logo">
            <h1>ALL CRYPTOCURRENCIES PRICES</h1>
        </div>

        <div class="header__hamburger">
            <img src="/images/svg/hamburger.svg" alt="hamburger-icon">
        </div>  
    </header>
</template>

<style>
    .header {
        margin: 20px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 150px;
    }

    .header__logo {
        margin-left: 100px;
        display: flex;
        align-items: center;

    }

    .header__logo img {
        width: 70px;
        margin-right: 30px;
    }

    .header__hamburger img {
        width: 30px;
        margin-right: 140px;
    }
</style>