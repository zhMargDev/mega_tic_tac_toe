<template>
    <div id="menuBarMain">
        <div class="radioBox">
            <h3>Режим игры</h3>
            <div class="inptBox" @click="selectGameMode('2players')" :class="{selected: gameMode === '2players'}">
                <h5 for="2players">2 Играка</h5>
            </div>
            <div class="inptBox" @click="selectGameMode('withBot')" :class="{selected: gameMode === 'withBot'}">
                <h5 for="withBot">С ботом</h5>
            </div>
        </div>
        <button id="start">Начать</button>
    </div>
</template>

<script>
export default{
    props:{
        gameMode: String
    },
    methods:{
        selectGameMode(gameMode){
            this.$emit('game-mode', gameMode);
        }
    }
}
</script>

<style scoped>
.radioBox{
    padding: 10px;
    padding-bottom: 20px;
}
.selected{
    background: #5454ff !important;
}
.inptBox{
    padding: 10px;
    border-radius: 10px;
    cursor: pointer;
    transition: 300ms;
}
.inptBox h5{
    margin: 0;
    font-size: 15px;
}
#menuBarMain{
    width: 200px;
    font-family: Sans;
}
#start{
    width: 100%;
    padding: 20px 0;
    font-size: 20px;
    font-weight: bold;
    font-family: Sans;
    background: rgba(0,255,150,1);
    color: #353535;
    border: 0;
    cursor: pointer;
    transition: 300ms;
}
#start:hover{
    background: rgba(0,255,38,1);
    box-shadow: 0 0 10px rgba(0,255,38,1);
}
h3{
    margin-bottom: 0;
}
</style>