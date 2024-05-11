<template>
    <div id="gameBox">
        <span id="blocker" v-if="gameWinner === 'noOne'">Ничья</span>
        <div id="blocker" v-if="gameWinner === 'o'"><img src="@/assets/svgs/o.svg"></div>
        <div id="blocker" v-if="gameWinner === 'x'"><img src="@/assets/svgs/x.svg"></div>
        <!-- <img src="@/assets/svgs/cells.svg" id="mainCells"> -->
        <MiniGame v-for="(mGame, index) in miniGames" :key="index" 
        :class="{
            'col1 row1': index === 0, 'col2 row1': index === 1, 'col3 row1': index === 2,
            'col1 row2': index === 3, 'col2 row2': index === 4, 'col3 row2': index === 5,
            'col1 row3': index === 6, 'col2 row3': index === 7, 'col3 row3': index === 8,
        }" 
        :readonly="!miniGamesTurn[index]" 
        :size="miniGamesSize" 
        :lattice="miniGames[index]" 
        @game="gameHandler" 
        :latticeRate="index" 
        :gameRate="gameRate" 
        :gameTurn="miniGamesTurn[index]" 
        :gameWinner="miniGameWinners[index]" 
        :gameBlockRate="gameBlockRate"
        />


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
            miniGames: [
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']],
                [['','',''],['','',''],['','','']]
        ],
            miniGameWinners: ['none','none','none','none','none','none','none','none','none'],
            miniGamesTurn: [true,true,true,true,true,true,true,true,true],
            mainLattice: [['','',''],['','',''],['','','']],
            gameBlockRate: -1,
            miniGamesSize: '140px',
            gameRate: 'x',
            gameWinner: ''
        }
    },
    methods:{
        gameHandler(data){
            // Поставить X или O на нажатой кнопке если она путсая, в противном случаи пропустить функцию
            if(this.miniGames[data.boxIndex][data.row][data.index] === ''){
                this.miniGames[data.boxIndex][data.row][data.index] = data.XorO;
            }else{return}

            // Смена хода 
            if (this.gameRate === 'x'){this.gameRate = 'o'}
            else if (this.gameRate === 'o'){this.gameRate = 'x'}

            // Проверка выграл ли кто то в маленькой игре
            const minGameWinner = this.checkWinner(this.miniGames[data.boxIndex]);

            // Если был победитель или была ничья зафиксировать
            if (minGameWinner !== null){
                this.miniGameWinners[data.boxIndex] = minGameWinner;
                if(minGameWinner !== 'noOne'){
                    this.mainLattice[Math.floor(data.boxIndex / 3)][data.boxIndex % 3] = minGameWinner;
                }
            }
            // Зафиксировать в каком боксе будет следующий шаг
            if(this.miniGameWinners[data.nextGameIndex - 1] === 'none'){
                this.gameBlockRate = data.nextGameIndex;
            }else{
                // Если бокс был выигран или в ничью, то дать выбор в каком боксе сыграть
                this.gameBlockRate = -1;
            }

            // Проверка кто выиграл всю игру
            const winner = this.checkWinner(this.mainLattice);
            if(winner !== null){this.gameWinner = winner}
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
#blocker{
    width: 100%;
    height: 100%;
    position: absolute;
    top: 50%;
    left: 50%;
    z-index: 1000;
    background: #000c;
    transform: translate(-50%, -50%);
    border-radius: 15px;
    display: flex;
    font-family: Sans;
    font-weight: bold;
    font-size: 50px;
    justify-content: center;
    align-items: center;
    color: lightgreen;
}
#blocker img{
    width: 70%;
    margin: auto;
}
#gameBox{
    display: flex;
    flex-wrap: wrap;
    position: relative;
    width: 440px;
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