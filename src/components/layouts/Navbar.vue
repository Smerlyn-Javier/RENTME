<template>
  <div :class="navScroll ? 'container' : 'container-scroll'">
    <div class="navbar">
      <div class="logo">
        <a href="#">
          <img class="img" src="../../assets/resources/lamborghini-logo.png" alt />
        </a>
      </div>

      <div class="nav-item">
        <a href="#" class="item" v-for="(menu,index) in menuOptions" :key="index">{{menu.name}}</a>
      </div>

      <div class="user">
        <!-- LOGUEADO -->
        <div class="login" v-if="log">
          <div class="user-name">
            <a href="#" @click="change">Juanito Alcachofa</a>
          </div>
          <div class="avatar">
            <img class="img" src="../../assets/resources/lamborghini-logo.png" alt />
          </div>
        </div>
        <!-- DESLOGEADO -->
        <div class="logout" v-if="!log">
          <button class="registrarse-button" @click="change">Registrate</button>
          <button class="iniciar-sesion-button">Iniciar Sesion</button>
        </div>
      </div>

      <!-- MENU WRAPPER -->
      <div id="sidemenu">
        <button class="sidemenu__btn" v-on:click="navOpen=!navOpen" v-bind:class="{active:navOpen}">
          <span class="top"></span>
          <span class="mid"></span>
          <span class="bottom"></span>
        </button>
        <transition name="translateX">
          <nav v-show="navOpen">
            <div class="sidemenu__wrapper">
              <ul class="sidemenu__list">
                <li v-for="(menu,index) in menuOptions" :key="index" class="sidemenu__item">
                  <a :href="menu.url">{{menu.name}}</a>
                </li>
                <li class="sidemenu__item" v-if="!log">
                  <a href="#">Iniciar sesion</a>
                </li>
                <li class="sidemenu__item" v-if="!log">
                  <a href="#">Registrate</a>
                </li>
                <li class="sidemenu__item" v-if="log">
                  <a href="#">Juanito Alcachofa</a>
                </li>
              </ul>
            </div>
          </nav>
        </transition>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "navar",
  data() {
    return {
      menuOptions: [
        { url: "#rentar", name: "Rentar un vehiculo" },
        { url: "#catalogo", name: "Catalogo de vehiculos" },
        { url: "#renta", name: "Renta tu vehiculo" }
      ],
      navOpen: false,
      navScroll: true,
      exe: true,
      log:true
    };
  },
  async created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    change(){
      this.log = !this.log
    },
    handleScroll() {
      const top = 0;
      const scroll = 50;

      if (window.scrollY >= scroll && this.exe) {
        this.exe = false;
        this.navScroll = !this.navScroll;
      } else if (window.scrollY === top) {
        this.exe = true;
        this.navScroll = !this.navScroll;
      }
    }
  }
};
</script>
<style lang="scss" scoped>
@import "../../assets/scss/mixins.scss";
.container-scroll {
  position: fixed;
  z-index: 1000;
  top: 0;
  width: 100%;
  box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.377);
}
.navbar {
  display: flex;
  justify-content: space-between;
  background-color: #181818;

  .nav-item {
    display: grid;
    background-color: inherit;
    grid-template-columns: repeat(3, 1fr);

    & .item {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
      border-bottom: 3px solid rgb(44, 44, 44);
    }
    & .item:hover {
      background-color: rgb(44, 44, 44);
      border-bottom: 2px solid white;
      transition: 0.5s;
    }
  }
  & .logo {
    height: 70px;
    display: grid;
    justify-content: center;
    align-items: center;
    margin: 20px;

    & .img {
      width: 60px;
    }
  }

  & .user {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 30%;
    & .login {
      width: 100%;
      height: 100px;
      display: flex;
      justify-content: flex-end;
      align-items: center;

      & .user-name {
        height: 70px;
        display: grid;
        justify-content: center;
        align-items: center;
        margin: 20px;
      }
      & .avatar {
        display: flex;
        margin-right: 20px;
        align-items: center;
        justify-content: center;
        background-color: white;
        padding: 20px;
        height: 30px;
        width: 30px;
        border-radius: 100%;
        &:hover {
          background-color: rgb(44, 44, 44);
          transition: 0.5s;
        }
        & .img {
          width: 40px;
        }
      }
    }

    & .logout {
      width: 100%;
      display: flex;

      & .user-name {
        height: 70px;
        display: grid;
        justify-content: center;
        align-items: center;
        margin: 20px;
      }
      & .avatar {
        & .img {
          width: 60px;
        }
      }

      & .registrarse-button {
        width: 100%;
        color: black;
        margin: 10px;
        height: 50px;
        border: 0px;
        font-size: 16px;
        border-radius: 1px;
        background-color: white;
        cursor: pointer;
        &:focus {
          outline: none;
          box-shadow: 0 0 3px #409eff;
        }
      }

      & .iniciar-sesion-button {
        width: 100%;
        color: white;
        margin: 10px;
        height: 50px;
        border: 0px;
        font-size: 16px;
        border-radius: 1px;
        background-color: #181818;
        cursor: pointer;
        &:hover {
          background-color: rgb(44, 44, 44);
          transition: 0.5s;
        }
        &:focus {
          outline: none;
          box-shadow: 0 0 3px #409eff;
        }
      }
    }
  }
}

#sidemenu {
  display: none;
}

@include respond-below(md) {
  .navbar {
    .nav-item {
      display: none;
    }
    .user {
      display: none;
    }
  }
  // MENU
  #sidemenu {
    display: flex;
    nav {
      width: 300px;
      background: #181818;
      position: fixed;
      top: 105px;
      left: 0;
      z-index: 99;
    }

    .sidemenu {
      &__btn {
        display: block;
        width: 50px;
        height: 100%;
        background: #181818;
        border: none;
        position: relative;
        z-index: 100;
        appearance: none;
        cursor: pointer;
        outline: none;

        span {
          display: block;
          width: 20px;
          height: 2px;
          margin: auto;
          background: white;
          position: absolute;
          top: 0;
          bottom: 0;
          left: 0;
          right: 0;
          transition: all 0.4s ease;

          &.top {
            transform: translateY(-8px);
          }

          &.bottom {
            transform: translateY(8px);
          }
        }
        &.active {
          .top {
            transform: rotate(-45deg);
          }
          .mid {
            transform: translateX(-20px) rotate(360deg);
            opacity: 0;
          }
          .bottom {
            transform: rotate(45deg);
          }
        }
      }

      &__wrapper {
        padding-top: 0px;
      }

      &__list {
        padding-top: 50px;
        list-style: none;
        padding: 0;
        margin: 0;
      }

      &__item {
        a {
          text-decoration: none;
          line-height: 1.6em;
          font-size: 1.6em;
          padding: 0.5em;
          display: block;
          color: white;
          transition: 0.4s ease;

          &:hover {
            background: #181818;
            color: rgb(44, 44, 44);
          }
        }
      }
    }
  }

  .translateX-enter {
    transform: translateX(-200px);
    opacity: 0;
  }

  .translateX-enter-active,
  .translateX-leave-active {
    transform-origin: top left 0;
    transition: 0.2s ease;
  }

  .translateX-leave-to {
    transform: translateX(-200px);
    opacity: 0;
  }
}
</style>