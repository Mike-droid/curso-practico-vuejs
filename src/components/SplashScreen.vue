<template>
  <div class="splashscreen">
    <img src="@/assets/cashflow-icon.svg" alt="cashflow logo" />
    <h1><span>Cash</span>Flow</h1>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.splashscreen {
  align-items: center;
  display: flex;
  flex-direction: column;
  height: 100vh;
  justify-content: center;
}

h1 {
  color: var(--brand-blue);
}

h1 span {
  color: var(--brand-green);
}
</style>