<template> 
  <div>
    <div class="row">
      <div class="col-sm">
        <p style="font-size: 150%">{{aPlayer.name}}</p>
        <p>
          <img v-bind:style="{width: aPlayer.hp + 'px'}" :src="hp1" alt height="20px" />
        </p>
        <p style="font-size: 150%">{{levelhp}}{{aPlayer.hp}}</p>
        <p>
          <img style="width:70%" :src="aPlayer.image" />
        </p>
      </div>
      <div class="col-sm">
        <div class="row">
          <div class="col-3">
            <button class="btn btn-outline-info" @click="start()">Start</button>
          </div>
          <div class="col-">
            <button v-bind:disabled="end" class="btn btn-danger" @click="attack()">Attack</button>
          </div>
          <div class="col-4">
            <button v-bind:disabled="end" class="btn btn-danger" @click="specialattack()">Special Attack</button>
          </div>
          <div class="col-">
            <button class="btn btn-outline-warning" @click="reset()">Restart</button>
          </div>
          <br /><br /><br /><br /><br /><br /><br />       

          <img
            class="rounded mx-auto d-block"
            src="https://lh3.googleusercontent.com/proxy/L8JTgCl5wRqdxceb1u4EQgpYBPp8g4Q4hQkfiEqI0QZ1anYXyw6JDG8I3CuUxJbp5-O1dijADuAHps-Ix1SmLi3PbT1vng2aW-CNpcC3avrfUXgttuZ9iE8"
            width="100%"
          />
        </div>
        <div class="row">
          <div class="col-sm"></div>
          <div class="col-sm">
            <div id="score">
              <div v-if="aMonster.hp <= 0">VICTORY</div>
              <div v-else-if="aPlayer.hp <= 0">DEFEAT</div>
            </div>
          </div>
          <div class="col-sm"></div>
        </div>
      </div>
      <div class="col-sm">
        <p style="font-size: 150%">{{aMonster.name}}</p>
        <p>
          <img v-bind:style="{width: aMonster.hp + 'px'}" :src="hp2" alt height="15px" />
        </p>
        <p style="font-size: 150%">{{levelhp}}{{aMonster.hp}}</p>
        <p>
          <img style="width:70%" :src="aMonster.image" />
        </p>
      </div>
    </div>
    <hr/>   
  </div>
</template>


// *** โครงสร้างมาตรฐาน ***
<script>
export default {
  data: function () {
    return {
      levelhp: "HP : ",
      end: false,
      hp1:"https://i.dlpng.com/static/png/4400382-health-bar-png-pictures-trzcacakrs-health-bar-png-1190_1120_preview.webp",
      hp2:"https://pngimage.net/wp-content/uploads/2018/06/health-bar-png-9.png",
      // ชื่อ player[1].name
      aPlayer: { name: "", hp: 1, image: "", hp1: "" },
      player: [
        { name: "Dr.Strange", hp: 250, image: require("../assets/dr_strange.png"), },
        { name: "Groot", hp: 210, image: require("../assets/groot.png"), },
        { name: "Iron man", hp: 300, image: require("../assets/ironman.png"), },
        { name: "Captain America", hp: 300, image: require("../assets/captain.png"), },
      ],
      aMonster: { name: "", hp: 1, image: "", hp1: "" },
      monster: [
        { name: "Red skull",hp: 230, image: require("../assets/redskull.png"), },
        { name: "Thanos", hp: 320, image: require("../assets/thanos2.png"), },
        { name: "Ultron", hp: 200, image: require("../assets/ultron.png"), },
        { name: "Magneto", hp: 250, image: require("../assets/magneto.png"), },
      ],
      pmax: "50%",
      mmax: "50% ",
    };
  },

  methods: {
    randomNo: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },

    start: function () {
      // 1. random Player 1-4 --> ชื่อ hp รูป
      this.aPlayer = this.player[this.randomNo(1, 4) - 1];
      // 2. random Monster 1-4
      this.aMonster = this.monster[this.randomNo(1, 4) - 1];
    },

    attack: function () {
      // 1. player โจมตี monster
      this.pmax = Math.floor(Math.random() * 10) + 3;
      this.aMonster.hp = this.aMonster.hp - this.pmax;
      // 2. monster โจมตี player
      this.mmax = Math.floor(Math.random() * 15) + 5;
      this.aPlayer.hp = this.aPlayer.hp - this.mmax;
      // 3. player.HP<=0  ===>?
      if (this.aPlayer.hp <= 0) {
        this.aPlayer.hp = 0;
        this.end = true;
        // 4. monster.HP<=0  ===>?
      } else if (this.aMonster.hp <= 0) {
        this.aMonster.hp = 0;
        // 5.END GAME
        this.end = true;
      }
    },
    specialattack: function () {
      // โจมตีด้วยท่าไม้ตาย
      this.pmax = Math.floor(Math.random() * 20) + 10;
      this.aMonster.hp = this.aMonster.hp - this.pmax;
      this.mmax = Math.floor(Math.random() * 15) + 5;
      this.aPlayer.hp = this.aPlayer.hp - this.mmax;
      if (this.aPlayer.hp <= 0) {
        this.aPlayer.hp = 0;
        this.end = true;
      } else if (this.aMonster.hp <= 0) {
        this.aMonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>

<style>
#score {
  font-size: 500%;
  color: rgb(229, 255, 0);
}
</style>