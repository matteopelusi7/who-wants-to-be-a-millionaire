<template>
  <div class="home">

    <div class="header">
      <figure class="image-logo">
        <img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0b8e1102-7ff4-4870-a39e-ef625253af75%2Flogo.png?table=block&id=d1419994-97c4-4690-b349-03db5eada926&spaceId=4c49ff97-016b-4669-8de5-4479dd1a86e1&width=480&userId=863850ea-3b24-4de8-b681-d214b9ffd42e&cache=v2" alt="">
      </figure>
    </div>

    <div class="footer">

    </div>

  </div>
</template>

<script>
export default {
  name: 'MainHome',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.home {
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.header {
  height: 40%;
  background-color: blue;
  display: flex;
  justify-content: center;
  align-items: center;

  .image-logo {
    img {
      width: 300px;
    }
  }
}

.footer {
  height: 60%;
  background-color: rgb(1, 1, 77);
}

</style>