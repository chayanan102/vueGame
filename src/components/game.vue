<template>
    <div>
        <p>HP Player {{randomNo(1,300)}}
           {{player[randomNo(1,3)-1].name}}
        </p> +รูป
            
        <p>HP Monster 150</p> +รูป
        <hr />
        name = {{ aPlayer.name }}
        hp = {{ aPlayer.hp }}
        <button @click='start'>Start</button>
        <button @click='attack'>Attack</button>
    </div>
</template>


// *** โครงสร้างมาตรฐาน ***
<script>
export default {
    data:function(){
        return{
            aPlayer:{ name: '', hp: 0, image: '' },
            // ชื่อ player[1].name
            player : [
                { name: 'Anakin', hp:90, image: '' },
                { name: 'Iron Man', hp:150, image: '' },
                { name: 'Doraeman', hp:200, image: '' },
                ],

            monster : [
                { name:'Thanos', hp:300, image: '' },
                { name:'Death vader', hp:20, image: '' },
                { name:'Prayuth', hp:1, image: '' },
                ],

        }
    },

    methods:{
        randomNo: function(min, max) {             
            return Math.max(Math.floor(Math.random() * max) + 1, min);    
        },

        start:function(){
            // 1. random Player 1-3 --> ชื่อ hp รูป
            this.aPlayer = this.player[this.randomNo(1,3)-1]
            // 2. random Monster 1-3
        },

        attack:function(){
            // 1. player โจมตี monster
            // 2. monster โจมตี player
            // 3. player.HP<=0  ===>?
            // 4. monster.HP<=0  ===>?
            // 5.END GAME

        }
    },

}
</script>

<style>

</style>