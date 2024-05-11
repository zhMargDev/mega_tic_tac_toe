<template>
    <div id="game_main_box" :style="{'height': size, 'width': size}">
        <span id="blocker" v-if="!gameTurn || gameWinner === 'noOne' || gameBlockRate !== latticeRate + 1 && gameBlockRate !== -1"></span>
        <div id="blocker" v-if="gameWinner === 'o'"><img src="@/assets/svgs/o.svg"></div>
        <div id="blocker" v-if="gameWinner === 'x'"><img src="@/assets/svgs/x.svg"></div>
        <!-- <img src="@/assets/svgs/cells.svg" id="background"> -->
        <div id="game_box">
            <button class="row1 col1" @click="step(0, 0, 1)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[0][0] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[0][0] === 'o'" class="card">
            </button>
            <button class="row1 col2" @click="step(0, 1, 2)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[0][1] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[0][1] === 'o'" class="card">
            </button>
            <button class="row1 col3" @click="step(0, 2, 3)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[0][2] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[0][2] === 'o'" class="card">
            </button>
            
            <button class="row2 col1" @click="step(1, 0, 4)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[1][0] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[1][0] === 'o'" class="card">
            </button>
            <button class="row2 col2" @click="step(1, 1, 5)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[1][1] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[1][1] === 'o'" class="card">
            </button>
            <button class="row2 col3" @click="step(1, 2, 6)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[1][2] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[1][2] === 'o'" class="card">
            </button>

            <button class="row3 col1" @click="step(2, 0, 7)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[2][0] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[2][0] === 'o'" class="card">
            </button>
            <button class="row3 col2" @click="step(2, 1, 8)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[2][1] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[2][1] === 'o'" class="card">
            </button>
            <button class="row3 col3" @click="step(2, 2, 9)">
                <img src="@/assets/svgs/x.svg" v-if="lattice[2][2] === 'x'" class="card">
                <img src="@/assets/svgs/o.svg" v-if="lattice[2][2] === 'o'" class="card">
            </button>
        </div>
    </div>
</template>

<script>
export default{
    props:{
        size: String,
        lattice: Object,
        latticeRate: Number,
        gameTurn: Boolean,
        gameWinner: String,
        gameRate: String,
        gameBlockRate: Number
    },
    methods:{
        step(row, index, nextGameIndex){
            this.$emit('game', {
                row: row, 
                index: index, 
                XorO: this.gameRate, 
                boxIndex: this.latticeRate,
                nextGameIndex: nextGameIndex
            });
        }
    }
}
</script>

<style scoped>
#blocker{
    width: 95%;
    height: 95%;
    position: absolute;
    top: 50%;
    left: 50%;
    z-index: 100;
    background: #0005;
    transform: translate(-50%, -50%);
    border-radius: 15px;
    display: flex;
}
#blocker img{
    width: 70%;
    margin: auto;
}
#game_main_box{
    position: relative;
}
#background{
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
}
#game_box{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    width: 90%;
    height: 90%;   
    position: absolute;
    z-index: 2;
    grid-gap: 0;
    padding: 5%;
}
button{
    background: transparent;
    border: 0;
    cursor: pointer;
    position: relative;
    width: 100%;
    height: 100%;
    margin: auto;
    display: flex;
}
.col1{
    border-right: 3px solid #626262;
}
.col2{
    border-right: 3px solid #626262;
    border-left: 3px solid #626262;
}
.col3{
    border-left: 3px solid #626262;
}
.row1{
    border-bottom: 3px solid #626262;
}
.row2{
    border-top: 3px solid #626262;
    border-bottom: 3px solid #626262;
}
.row3{
    border-top: 3px solid #626262;
}
@keyframes card_show_anim{
    0%{opacity: 0;}
    100%{opacity: 1;}
}
.card{
    animation: card_show_anim 300ms;
    width: 70%;
    height: 70%;
    margin: auto;
}
</style>