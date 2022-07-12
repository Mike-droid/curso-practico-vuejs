<template>
  <main>
    <p>{{ selectedDate }}</p>
    <h1>{{ amountCurrency }}</h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script setup>
import { toRefs, defineProps, computed } from "vue";

const currencyFormatter = new Intl.NumberFormat("es-MX", {
  style: "currency",
  currency: "MXN",
});

const props = defineProps({
  label: {
    type: String,
    required: true,
  },
  dateLabel: {
    type: String,
    default: null,
  },
  totalAmount: {
    type: Number,
    required: true,
  },
  amount: {
    type: Number,
    default: null,
  },
});

const { label, dateLabel, totalAmount, amount } = toRefs(props);

const amountVisual = computed(() =>
  amount.value !== null ? amount.value : totalAmount.value
);

const selectedDate = computed(() =>
  dateLabel.value !== null ? dateLabel.value : label.value
);

const amountCurrency = computed(() =>
  currencyFormatter.format(amountVisual.value)
);
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}
h1,
p {
  margin: 0;
  text-align: center;
}
h1 {
  margin-top: 14px;
  color: var(--brand-green);
}
.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>