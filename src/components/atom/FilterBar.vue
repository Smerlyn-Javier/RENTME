<template>
  <div class="container">
    <div class="searh-bar">
      <div class="bar-container">
        <input class="bar" type="text" placeholder="¿Que andas buscando?" />
      </div>

      <div class="filter-button">
        <div class="buttons" v-for="(logo,index) in logos" :key="index">
          <img class="img" :src="logo.url" alt />
        </div>
      </div>

      <div class="public-car">
        <button class="pulic-button">Pulica tu vehiculo</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "filter-bar",
  data() {
    return {
      input: "",
      logos:[
          {url:require('../../assets/icons/audi.svg')},
          {url:require('../../assets/icons/mazda.svg')},
          {url:require('../../assets/icons/honda.svg')},
          {url:require('../../assets/icons/mercedez-logo.svg')},
          {url:require('../../assets/icons/toyota.svg')},
      ]
    };
  }
};
</script>
<style lang="scss" scoped>
.searh-bar {
  & .bar-container {
    width: 100%;
    height: 50px;
    & .bar {
      font-size: 20px !important;
      padding: 10px;
      width: 96%;
      border-radius: 4px;
      border: 1px solid rgb(226, 226, 226);
      &:hover {
        border: 1px solid rgba(189, 189, 189, 0.842);
      }
      &:focus {
        border: 1px solid white;
        border-radius: 4px;
        outline: none;
        box-shadow: 0 0 3px #409eff;
      }
    }
  }

  & .filter-button {
    width: 100%;
    display: flex;
    // background-color: violet;
    padding-top: 10px;
    padding-bottom: 10px;
    :hover {
      box-shadow: 0 0 3px #409eff;
    }

    & .buttons {
      display: flex;
      justify-content: center;
      align-items: center;
      min-width: 80px;
      min-height: 80px;
      margin: 20px;
      border-radius: 4px;
      background-color: white;
      box-shadow: 0 0 3px #d8d8d8;

      & .img {
        height: 40px;
        &:hover {
          box-shadow: none;
        }
      }
    }
  }

  & .public-car {
    & .pulic-button {
      width: 100%;
      color: white;
      height: 50px;
      border: 0px;
      font-size: 16px;
      border-radius: 4px;
      background-color: #181818;
      cursor: pointer;
      &:focus {
        outline: none;
        box-shadow: 0 0 3px #409eff;
      }
    }
  }
}
</style>