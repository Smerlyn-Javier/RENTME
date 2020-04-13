<template>
  <div class="container">
    <div class="hero">
      <div class="filter">
            <h2 class="title">¿Buscas un vehiculo en Santo Domingo?</h2>
          <filter-bar />
      </div>
    </div>
  </div>
</template>

<script>
import FilterBar from "./atom/FilterBar";
export default {
  name: "hero",
  components: {
    FilterBar
  }
};
</script>
<style lang="scss" scoped>
.hero {
  display: flex;
  align-items: center;
  justify-content: center;
  background-image: url('https://drscdn.500px.org/photo/1007037307/q%3D80_m%3D2000/v2?sig=1c7ebbac5383de84721d3e979615618d0f65b4b51b1135fff4b39af49f02967d');
  height: 900px;

  & .filter {
    height: 325px;
    width: 600px;
    border-radius: 4px;
    padding: 20px;
    background-color: white;
    & .title{
        text-align: center;
        padding: 20px;
        font-size: 20px;
    }
  }
}
</style>
