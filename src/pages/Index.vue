<template>
  <q-page class="flex flex-center">
    <div class="container">
      <div>
        <div class="generalFloor">
          <div class="floor d-flex justify-content-center align-items-center" style="background-color: #ccc;">
              <div class="player" id="triangulo-para-direita"></div>
          </div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="commands">
              <input type="text" class="inputComand" placeholder="Digite um comando!">
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex'
}
</script>

<style scoped>
  body{
    padding: 30px;
  }

  .generalFloor{
    width: 300px;
    height: 360px;
  }
  .floor{
    width: 100px;
    height: 100px;
    position: relative;
    float: left;
    border: 1px solid #999;
  }
  .commands{
    width: 300px;
    height: 50px;
    position: relative;
    float: left;
    margin-top: 10px;
  }
  .inputComand{
    width: 100%;
    height: 100%;
  }

  #triangulo-para-cima {
    width: 0;
    height: 0;
    border-left: 15px solid transparent;
    border-right: 15px solid transparent;
    border-bottom: 15px solid #333;
  }

  #triangulo-para-direita {
    width: 0;
    height: 0;
    border-top: 15px solid  transparent;
    border-bottom: 15px solid  transparent;
    border-left: 15px solid #333;
  }

  #triangulo-para-baixo {
    width: 0;
    height: 0;
    border-left: 15px solid transparent;
    border-right: 15px solid transparent;
    border-top: 15px solid #333;
  }

  #triangulo-para-esquerda {
    width: 0;
    height: 0;
    border-top: 15px solid transparent;
    border-bottom: 15px solid transparent;
    border-right:15px solid #333;
  }
</style>
