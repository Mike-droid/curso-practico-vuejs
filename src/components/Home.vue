<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume
        :label="'Ahorro total'"
        :totalAmount="totalAmount"
        :amount="amount"
        :dateLabel="dateLabel"
      >
        <template #graphic>
          <Graphic :amounts="amounts" @select="select" />
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
      movements: [],
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
        const lastMovements = lastDays.slice(0, index + 1);

        return lastMovements.reduce((suma, movement) => {
          return suma + movement;
        }, 0);
      });
    },

    totalAmount() {
      return this.movements.reduce((suma, m) => {
        return suma + m.amount;
      }, 0);
    },
  },

  mounted() {
    const movements = JSON.parse(localStorage.getItem("movements"));

    if (Array.isArray(movements)) {
      this.movements = movements?.map((m) => {
        return { ...m, time: new Date(m.time) };
      });
    }
  },

  methods: {
    create(movement) {
      this.movements.push(movement);
      this.save();
    },

    remove(id) {
      const index = this.movements.findIndex((m) => m.id === id);
      this.movements.splice(index, 1);
      this.save();
    },

    save() {
      localStorage.setItem("movements", JSON.stringify(this.movements));
    },

    select(element) {
      this.amount = element;
    },
  },
};
</script>