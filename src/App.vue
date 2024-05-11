<template>
    <div id="mainBox">
        <GameComponent />
        <MenuBar :gameMode="gameMode" @game-mode="gameModeChangeHandler" />
    </div>
</template>

<script>
import MenuBar from '@/components/MenuBar.vue'
import GameComponent from '@/components/GameComponent.vue'

export default {
    name: 'App',
    components: {
        MenuBar,
        GameComponent
    },
    data(){
        return{
            gameMode: '2players'
        }
    },
    methods:{
        gameModeChangeHandler(gameMode){
            this.gameMode = gameMode;
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
#mainBox{
    display: flex;
    justify-content: center;
}
</style>