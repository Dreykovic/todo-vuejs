<template>
  <div id="app">
    <h4 class="title">La TO DO liste de {{ nom }}</h4>
    <div class="container-task">
      <div class="ligne">
        <div class="titre-colonne-1">Tâche</div>

        <div class="titre-colonne-1">Effectuée</div>
      </div>
      <div class="ligne" v-for="task in tasks" v-bind:key="task.action">
        <div class="colonne-1">{{ task.action }}</div>

        <div class="colonne-2">{{ task.faite }}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "app",
  data() {
    return {
      nom: "Drey",
      tasks: [
        { action: "Finir le diagramme de classes", faite: false },
        { action: "Concevoirla vidéo du projet", faite: false },
        { action: "Debogger le code", faite: true },
        { action: "Finir le Tp de Laravel", faite: false },
      ],
    };
  },
};
</script>
<style>
/*app stylle*/
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
}
/*app title style*/
#app > h4.title {
  background: dodgerblue;
  width: 100%;
  height: 100px;
  text-align: center;
  color: white;
  font-size: large;
}
/**task display style */
#app .container-task{
  padding: 50px;
  width: 80%;
}
</style>
