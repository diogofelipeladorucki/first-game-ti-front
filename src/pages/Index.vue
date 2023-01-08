<template>
  <q-page class="flex flex-center">
    <div class="container">
      <div>
        <pre>
        <!-- {{floor}} -->

        </pre>
        <div class="generalFloor">
          <div v-for="(row, index) in floor" :key="index">
            <div v-for="(col, i) in row" :key="i+'i'">
              <div class="floor" style="background-color: #ccc;">
                <!-- {{col.here}} -->
                <div v-if="col.here" class="player" :id="getDirection"></div>
              </div>
            </div>
          </div>
          
          <!-- <div v-for="(row, index) in floor" :key="index">
            <div v-for="(c, i) in row" :key="i+'index'" class="floor d-flex justify-content-center align-items-center" style="background-color: #ccc">
              {{c}}
              <div class="floor" style="background-color: #ccc;"></div>
            </div>
          </div> -->
          <!-- <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div>
          <div class="floor" style="background-color: #ccc;"></div> -->
          <div class="commands">
              <input v-model="command" type="text" class="inputComand" placeholder="Digite um comando!" @keypress="setCommand">
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      command: '',
      player: {
        name: 'Player',
        score: 0,
        direction: 'N'
      },
      floor: [],
      listCommands: ['ten', 'get', 'left', 'right', 'go'],
    }
  },
  computed: {
    getDirection(){
      if(this.player.direction == 'N'){
        return 'triangulo-para-cima'
      }else if(this.player.direction == 'E'){
        return 'triangulo-para-direita'
      }else if(this.player.direction == 'S'){
        return 'triangulo-para-baixo'
      }else if(this.player.direction == 'W'){
        return 'triangulo-para-esquerda'
      }
    }
  },
  beforeMount () {
    this.floor = this.createFloor()
  },
  methods: {
    createFloor () {
      let floor = [
        [this.createBox(),this.createBox(),this.createBox()],
        [this.createBox(true),this.createBox(),this.createBox()],
        [this.createBox(),this.createBox(),this.createBox()]
      ]
      return floor
    },
    createBox(bool = false){

      return {
        here: bool,
         // commands: ['ten', 'get', 'left', 'right', 'go'],
        // navigation: true,
        // itens: ['key', 'sword', 'shield', 'potion', 'food', 'gold'],
        }
    },
    setCommand(key){
      if(key.key != 'Enter'){
        return
      }
      if(this.listCommands.includes(this.command)){
        this[this.command]()
      }

      this.command = ''
    },
    left(){
      if(this.player.direction == 'N'){
        this.player.direction = 'W'
      }else if(this.player.direction == 'W'){
        this.player.direction = 'S'
      }else if(this.player.direction == 'S'){
        this.player.direction = 'E'
      }else if(this.player.direction == 'E'){
        this.player.direction = 'N'
      }
    },
    right(){
      if(this.player.direction == 'N'){
        this.player.direction = 'E'
      }else if(this.player.direction == 'E'){
        this.player.direction = 'S'
      }else if(this.player.direction == 'S'){
        this.player.direction = 'W'
      }else if(this.player.direction == 'W'){
        this.player.direction = 'N'
      }
    },
    go(){
     
    }
  }
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
