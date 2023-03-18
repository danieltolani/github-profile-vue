<template>
    <div class="about">
        <h1>About</h1>
        <p>
             This is a mini portfolio list of all my repositories on GitHub. <br/> This was created for my third semester, ⚡️ Altschool Africa examination 📕
        </p>
    </div>
</template>

<script>
export default {
    name: 'AboutComponent'
}
</script>

<style lang="scss" scoped>
.about {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 90vh;

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
    }

    a {
        color: #083042;
        text-decoration: none;
        text-decoration: underline;
    }
}
</style>