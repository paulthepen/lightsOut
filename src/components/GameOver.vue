<template>
<teleport to="body">
    <section v-if="this.type != null">
      <div class="backdrop"></div>
      <div class="modal">
        <header>
          <h2>{{ type == 'won' ? 'Victory!' : 'Game Over...' }}</h2>
        </header>
        <main>
          {{ gameOverStatus }}
        </main>
        <nav>
          <button @click="this.$emit('reset')">Play Again</button>
        </nav>
      </div>
    </section>
</teleport>
</template>

<script>
export default {
  props: ['round', 'type'],
  computed: {
    gameOverStatus() {
      if (this.type == 'won') {
        return 'Lights out in ' + this.round + ' tries!';
      } else if (this.type == 'lost') {
        return "I'm blinded!";
      } else {
        return '';
      }
    },
  },
};
</script>

<style scoped>
.backdrop {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 9;
}
.modal {
    position: absolute;
    width: 300px;
    border: 1px solid black;
    border-radius: 10px;
    box-shadow: 2px 2px 2px #000;
    z-index: 10;
    top: 100px;
    left: calc(50% - 170px);
    background-color: rgba(255,255,255,1);
    padding: 16px;
}

header {
    text-align: center;
}
nav {
    margin-top: 20px;
    text-align: center;
}
main {
    padding: 15px;
    text-align: center;
}
</style>
