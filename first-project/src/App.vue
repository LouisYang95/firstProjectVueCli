<template>
  <div class="container">
    <div class="row">
      <h1>CRYPTO</h1>
      <input
        type="text"
        class="form-control bg-dark text-light rounded-0 border-0 my-4"
        placeholder="Look for a coin"
        @keyup="searchCoin()"
        v-model="textSearch"
      />
      <table class="table table-dark">
        <thead>
          <tr>
            <th v-for="title in titles" :key="title">{{ title }}</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(coin, index) in filtredCoins" :key="coin.id">
            <td class="text-muted">{{ index + 1 }}</td>
            <td>
              <img :src="coin.image" style="width: 2rem" class="me-2" alt="" />
              <span>
                {{ coin.name }}
              </span>
              <span class="ms-2 text-uppercase text-muted">
                {{ coin.symbol }}
              </span>
            </td>
            <td>${{ coin.current_price }}</td>
            <td
              :class="[
                coin.price_change_percentage_24h > 0
                  ? 'text-success'
                  : 'text-danger',
              ]"
            >
              {{ coin.price_change_percentage_24h }}%
            </td>
            <td>${{ coin.total_volume }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      coins: [],
      filtredCoins: [],
      titles: ["#", "Coin", "price", "Price Change", "24 Volume"],
      textSearch: "",
    };
  },
  async mounted() {
    const res = await fetch(
      "https://api.coingecko.com/api/v3/coins/markets?vs_currency=eur&order=market_cap_desc&per_page=100&page=1&sparkline=false"
    );
    const data = await res.json();
    console.log(data);
    this.coins = data;
    this.filtredCoins = data;
  },
  methods: {
    searchCoin() {
      this.filtredCoins = this.coins.filter(
        (coin) =>
          coin.name.toLowerCase().includes(this.textSearch.toLowerCase()) ||
          coin.symbol.toLowerCase().includes(this.textSearch.toLowerCase())
      );
    },
  },
};
</script>

<style></style>
