<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume
        :label="'Ahorro total'"
        :totalAmount="50000"
        :amount="amount"
        :dateLabel="dateLabel"
      >
        <template #graphic> graphic </template>
        <template #action> action </template>
      </Resume>
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

<script>
import Header from "./Header.vue";
import Layout from "./Layout.vue";
import Movements from "./Movements.vue";
import Resume from "./Resume/Index.vue";

export default {
  components: {
    Header,
    Layout,
    Movements,
    Resume,
  },

  data() {
    return {
      amount: null,
      dateLabel: "22/10/2022",
    };
  },
};
</script>