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
        <template #graphic>
          <Graphic :amounts="amounts" />
        </template>
        <template #action>
          <Action />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" />
    </template>
  </Layout>
</template>

<script>
import Header from "./Header.vue";
import Layout from "./Layout.vue";
import Movements from "./Movements/Index.vue";
import Resume from "./Resume/Index.vue";
import Action from "./Action.vue";
import Graphic from "./Resume/Graphic.vue";

export default {
  components: {
    Header,
    Layout,
    Movements,
    Resume,
    Action,
    Graphic,
  },

  data() {
    return {
      amount: null,
      dateLabel: "22/10/2022",
      amounts: [100, 200, 500, 200, -400, -200, 300, 0, -500],
      movements: [
        {
          id: 1,
          title: "movement 1",
          description: "movement 1",
          amount: 100,
        },
        {
          id: 2,
          title: "movement 2",
          description: "movement 2",
          amount: 200,
        },
        {
          id: 3,
          title: "movement 3",
          description: "movement 3",
          amount: 300,
        },
        {
          id: 4,
          title: "movement 4",
          description: "movement 4",
          amount: 400,
        },
        {
          id: 5,
          title: "movement 5",
          description: "movement 5",
          amount: -400,
        },
      ],
    };
  },
};
</script>