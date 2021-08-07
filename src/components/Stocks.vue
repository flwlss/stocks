<template>
  <div class="stock">
    <div class="stock-item" v-for="value in stock" :key="value.stock">
      <div class="stock-item__info">
        <div class="stock-item__cover">
          <a :href="value.website" target="blank">
            <img :src="value.image" :alt="value.companyName" />
          </a>
        </div>
        <h3 class="stock-item__title">
          {{ value.companyName }}
          <span class="">{{ value.symbol }}</span>
        </h3>
      </div>
      <span class="stock-item__price">${{ value.price }}</span>
    </div>
  </div>

  <h3>Get Info</h3>
  <select v-model="selected">
    <option value="" disabled>Select Company</option>
    <option
      v-for="value in stock"
      :key="value.stock"
      :value="value.description"
    >
      {{ value.companyName }}
    </option>
  </select>
  <div class="stock-description">
    {{ selected }}
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Stocks",
  data() {
    return {
      stock: [],
      selected: "",
    };
  },
  created() {
    axios
      .get(
        "https://financialmodelingprep.com/api/v3/profile/AAPL,NVDA,TSLA,AMD,INTC,MDB,SPCE,V,DAL,DOCU,OKTA,AMZN,PINS,TRIP,GDDY,DIS,MCD,NOK,UPWK,IBM,FB,ZM,OZON,NFLX,EA,HLT,H,CCL?apikey=6c9be8fcb7df7894ba5ae48be14935fc"
      )
      .then((response) => {
        this.stock = response.data;
      });
  },
};
</script>