<template>
  <header class="header">
    <h2>Weather Application</h2>
    <p>{{ username }}님 반갑습니다.</p>
  </header>
</template>

<script>
export default {
  name: "HeaderDisplay",
  setup() {
    const username = "docker";

    return {
      username,
    };
  },
};
</script>

<style scoped>
.header {
  background: linear-gradient(to left, #3a1c71, #d76d77, #ffaf7b);
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h2 {
  color: #fff;
  padding: 0.5em;
}
.header p {
  font-size: 12px;
  color: #fff;
}
</style>
