<template>
    <div class="home">
        <h1>HI THERE! 👋🏽</h1>
        <p>This project is built on <a href="https://vuejs.org/" target="_blank">Vue.js</a> with ❤️ and 🔦</p>
        <button>
            <RouterLink to="/repos">open portfolio</RouterLink>
        </button>
    </div>
</template>

<script setup>
import { RouterLink } from 'vue-router'
</script>

<style lang="scss" scoped>
.home {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 80vh;

    h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
        font-family: "integral";
        font-weight: 200;
    }

    p {
        color: #2E3840;
        text-align: center;
         max-width: 30em;
      margin: 0 auto;
      line-height: 26px;
      font-size: 1.2rem;
      margin-bottom: 3rem;

      a {
        color: #083042;
        text-decoration: none;
        text-decoration: underline;
    }
    }

    button {
        padding: 1rem 2rem;
        border: none;
        background-color: #4183F2;
        color: #fff;
        font-size: 1.2rem;
        border-radius: 5px;
        text-transform: uppercase;
        cursor: pointer;
        font-family: 'integral';

        a {
        text-decoration: none;
        color: #fff;
    }

        &:hover {
            background-color: #083042;
        }
    }

   
}
</style>