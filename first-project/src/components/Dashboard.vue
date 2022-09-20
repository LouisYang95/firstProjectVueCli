<template>
  <div class="Dashboard">
    <h1>Dasboard Top 100 Cryptomonnaie :</h1>
    <div class="table">
      <table>
        <tr class="list-crypto" v-for="crypto in Top100Crypto" :key="crypto.id">
          <td>
            <img class="list-crypto-image" :src="crypto.image" />
          </td>
          <td>
            <div class="list-crypto-item__name">{{ crypto.name }}</div>
          </td>
          <td>
            <div class="list-crypto-item__price">
              {{ crypto.current_price }}
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "CryptoDashboard",
  data() {
    return {
      Top100Crypto: [],
    };
  },
  methods: {
    getCrypto() {
      fetch(
        "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false"
      )
        .then((response) => response.json())
        .then((data) => {
          for (let crypto in data) {
            this.Top100Crypto.push(data[crypto]);
            console.log(this.Top100Crypto);
          }
          return this.Top100Crypto;
        });
    },
  },
  mounted() {
    this.getCrypto();
  },
};
</script>

<style scoped>
.Dashboard {
  margin: 1em;
}
.list-crypto {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.list-crypto-image {
  width: 50px;
  height: 50px;
}
.table{
    display: flex;
    justify-content: center;
}
</style>
