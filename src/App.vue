<template>
    <div id="gameBox">
        <!-- <img src="@/assets/svgs/cells.svg" id="mainCells"> -->
        <MiniGame class="col1 row1" :size="miniGamesSize" :lattice="miniGame1" @game="gameHandler" :latticeRate="1" :gameRate="gameRate" :gameTurn="miniGame1Turn" :gameWinner="miniGame1Winner" />
        <MiniGame class="col2 row1" :size="miniGamesSize" :lattice="miniGame2" @game="gameHandler" :latticeRate="2" :gameRate="gameRate" :gameTurn="miniGame2Turn" :gameWinner="miniGame2Winner" />
        <MiniGame class="col3 row1" :size="miniGamesSize" :lattice="miniGame3" @game="gameHandler" :latticeRate="3" :gameRate="gameRate" :gameTurn="miniGame3Turn" :gameWinner="miniGame3Winner" />
        <MiniGame class="col1 row2" :size="miniGamesSize" :lattice="miniGame4" @game="gameHandler" :latticeRate="4" :gameRate="gameRate" :gameTurn="miniGame4Turn" :gameWinner="miniGame4Winner" />
        <MiniGame class="col2 row2" :size="miniGamesSize" :lattice="miniGame5" @game="gameHandler" :latticeRate="5" :gameRate="gameRate" :gameTurn="miniGame5Turn" :gameWinner="miniGame5Winner" />
        <MiniGame class="col3 row2" :size="miniGamesSize" :lattice="miniGame6" @game="gameHandler" :latticeRate="6" :gameRate="gameRate" :gameTurn="miniGame6Turn" :gameWinner="miniGame6Winner" />
        <MiniGame class="col1 row3" :size="miniGamesSize" :lattice="miniGame7" @game="gameHandler" :latticeRate="7" :gameRate="gameRate" :gameTurn="miniGame7Turn" :gameWinner="miniGame7Winner" />
        <MiniGame class="col2 row3" :size="miniGamesSize" :lattice="miniGame8" @game="gameHandler" :latticeRate="8" :gameRate="gameRate" :gameTurn="miniGame8Turn" :gameWinner="miniGame8Winner" />
        <MiniGame class="col3 row3" :size="miniGamesSize" :lattice="miniGame9" @game="gameHandler" :latticeRate="9" :gameRate="gameRate" :gameTurn="miniGame9Turn" :gameWinner="miniGame91Winner" />
    </div>
</template>

<script>
import MiniGame from '@/components/MiniGame.vue'

export default {
    name: 'App',
    components: {
        MiniGame
    },
    data(){
        return{
            miniGame1: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame1Winner: 'none',
            miniGame1Turn: false,

            miniGame2: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame2Winner: 'none',
            miniGame2Turn: false,

            miniGame3: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame3Winner: 'none',
            miniGame3Turn: false,

            miniGame4: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame4Winner: 'none',
            miniGame4Turn: false,

            miniGame5: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame5Winner: 'none',
            miniGame5Turn: false,

            miniGame6: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame6Winner: 'none',
            miniGame6Turn: false,

            miniGame7: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame7Winner: 'none',
            miniGame7Turn: false,

            miniGame8: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame8Winner: 'none',
            miniGame8Turn: false,

            miniGame9: [['','',''],['','',''],['','',''],{winner: 'none'}],
            miniGame9Winner: 'none',
            miniGame9Turn: false,

            mainLattice: [['','',''],['','',''],['','','']],
            gameRate: 1,
            miniGamesSize: '140px'
        }
    },
    methods:{
        gameHandler(data){
            if (data[3] === 1){
                if (this.miniGame1[data[0]][data[1]] === ''){
                    this.miniGame1[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame1);
                    if (winner === 'x'){this.miniGame1Winner = 'x'}
                    else if (winner === 'o'){this.miniGame1Winner = 'o'}
                    else if (winner === 'noOne'){this.miniGame1Winner = 'noOne'}
                }
            }else if (data[3] === 2){
                if (this.miniGame2[data[0]][data[1]] === ''){
                    this.miniGame2[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame2);
                    console.log(winner)
                }
            }else if (data[3] === 3){
                if (this.miniGame3[data[0]][data[1]] === ''){
                    this.miniGame3[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame3);
                    console.log(winner)
                }
            }else if (data[3] === 4){
                if (this.miniGame4[data[0]][data[1]] === ''){
                    this.miniGame4[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame4);
                    console.log(winner)
                }
            }else if (data[3] === 5){
                if (this.miniGame5[data[0]][data[1]] === ''){
                    this.miniGame5[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame5);
                    console.log(winner)
                }
            }else if (data[3] === 6){
                if (this.miniGame6[data[0]][data[1]] === ''){
                    this.miniGame6[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame6);
                    console.log(winner)
                }
            }else if (data[3] === 7){
                if (this.miniGame7[data[0]][data[1]] === ''){
                    this.miniGame7[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame7);
                    console.log(winner)
                }
            }else if (data[3] === 8){
                if (this.miniGame8[data[0]][data[1]] === ''){
                    this.miniGame8[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame8);
                    console.log(winner)
                }
            }else if (data[3] === 9){
                if (this.miniGame9[data[0]][data[1]] === ''){
                    this.miniGame9[data[0]][data[1]] = data[2];
                    const winner = this.checkWinner(this.miniGame9);
                    console.log(winner)
                }
            }
        },
        checkWinner(game) {
            // Проверка по горизонтали
            for (let row = 0; row < 3; row++) {
                if (game[row][0] === game[row][1] && game[row][1] === game[row][2] && game[row][0] !== '') {
                    return game[row][0];
                }
            }

            // Проверка по вертикали
            for (let col = 0; col < 3; col++) {
                if (game[0][col] === game[1][col] && game[1][col] === game[2][col] && game[0][col] !== '') {
                    return game[0][col];
                }
            }

            // Проверка по диагоналям
            if (game[0][0] === game[1][1] && game[1][1] === game[2][2] && game[0][0] !== '') {
                return game[0][0];
            }
            if (game[0][2] === game[1][1] && game[1][1] === game[2][0] && game[0][2] !== '') {
                return game[0][2];
            }

            if (game[0].every(cell => cell !== '') && game[1].every(cell => cell !== '') && game[2].every(cell => cell !== '')) {
                return 'noOne';
            }

            return null; // Нет победителя
        }
    }
}
</script>


<style>
body{
    padding: 0;
    margin: 0;
}
</style>

<style scoped>
#gameBox{
    display: flex;
    flex-wrap: wrap;
    position: relative;
    width: 500px;
    margin: 20px;
}
#mainCells{
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
}
.col1{
    border-right: 5px solid #626262;
}
.col2{
    border-right: 5px solid #626262;
    border-left: 5px solid #626262;
}
.col3{
    border-left: 5px solid #626262;
}
.row1{
    border-bottom: 5px solid #626262;
}
.row2{
    border-top: 5px solid #626262;
    border-bottom: 5px solid #626262;
}
.row3{
    border-top: 5px solid #626262;
}

</style>