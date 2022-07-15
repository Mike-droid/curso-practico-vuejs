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
          <Action @create="create" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements @remove="remove" :movements="movements" />
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
      movements: [
        {
          id: 1,
          title: "movement 1",
          description: "movement 1",
          amount: 100,
          time: new Date("07-01-2022"),
        },
        {
          id: 2,
          title: "movement 2",
          description: "movement 2",
          amount: 200,
          time: new Date("07-02-2022"),
        },
        {
          id: 3,
          title: "movement 3",
          description: "movement 3",
          amount: 300,
          time: new Date("07-03-2022"),
        },
        {
          id: 4,
          title: "movement 4",
          description: "movement 4",
          amount: 400,
          time: new Date("07-04-2022"),
        },
        {
          id: 5,
          title: "movement 5",
          description: "movement 5",
          amount: -400,
          time: new Date("07-05-2022"),
        },
      ],
    };
  },
  computed: {
    amounts() {
      const lastDays = this.movements
        .filter((m) => {
          const today = new Date();
          const oldDate = today.setDate(today.getDate() - 30);

          return m.time > oldDate;
        })
        .map((m) => m.amount);

      return lastDays.map((m, index) => {
        const lastMovements = lastDays.slice(0, index);

        return lastMovements.reduce((suma, movement) => {
          return suma + movement;
        }, 0);
      });
    },
  },
  methods: {
    create(movement) {
      this.movements.push(movement);
    },
    remove(id) {
      const index = this.movements.findIndex((m) => m.id === id);
      this.movements.splice(index, 1);
    },
  },
};
</script>