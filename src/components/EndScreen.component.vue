<template>
  <div
    v-if="status === 'WIN'"
    class="end-screen"
  >
    <div class="pop-up">
      <h4>Jeu gagné en {{ count }} coups.</h4>
      <button
        class="reload-game"
        @click="restart"
      >
        Restart
      </button>
    </div>
  </div>
</template>
<script>
import { mapGetters, mapMutations } from 'vuex';

export default {
  name: 'EndScreen',
  computed: {
    ...mapGetters(['count', 'status']),
  },
  methods: {
    ...mapMutations(['START_GAME']),
    restart() {
      this.START_GAME();
    },
  },
};
</script>

<style scoped>
    .end-screen {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(100, 100, 100, 0.4);
        z-index: 1000;
        display: flex;
    }

    .pop-up {
        margin: auto auto;
        min-width: 400px;
        background-color: white;
        border-radius: 4px;
        border: 1px solid #aaa;
        padding: 8px;
        box-sizing: border-box;
    }
    .reload-game {
        background-color: #ffc74e;
        padding: 8px 16px;
        border-radius: 4px;
        border: 1px solid rgb(255, 207, 70);
        color: rgba(255, 255, 255, 0.90);
        cursor: pointer;
        transition: 0.2s all ease;
    }
    .reload-game:hover {
        box-shadow: 0 0 3px #aaa;
    }

</style>
