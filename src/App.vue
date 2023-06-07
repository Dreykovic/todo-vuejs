<template>
  <div id="app">
    <h4 class="title">La TO DO liste de {{ nom }}</h4>
    <div class="container-task">
      <div class="ligne">
        <div class="titre-colonne titre-colonne-1">Tâche</div>

        <div class="titre-colonne titre-colonne-2">Effectuée</div>
      </div>
      <div class="ligne" v-for="task in filteredTasks" v-bind:key="task.action">
        <div class="colonne-1">{{ task.action }}</div>

        <div class="colonne-2">
          <input type="checkbox" v-model="task.faite" class="check-task" />{{
            task.faite
          }}
        </div>
      </div>
      <div class="ligne">
        <div class="add colonne-1">
          <input v-model="newItemText" class="input-task" v-on:keyup.enter="addNewTodo"/>
        </div>
        <div class="colonne-2">
          <button class="btn-add-task" v-on:click="addNewTodo">Add</button>
        </div>
      </div>
      <div class="container-filtre">
        <div class="filtre-content">
          <input type="checkbox" v-model="hideCompleted" id="filtrer" />
          <label for="filtrer"> Hide completed tasks </label>
        </div>
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
      hideCompleted: true,
      newItemText: "",
    };
  },
  computed: {
    filteredTasks() {
      return this.hideCompleted
        ? this.tasks.filter((task) => !task.faite)
        : this.tasks;
    },
  },
  methods: {
    addNewTodo() {
      this.tasks.push({ action: this.newItemText, faite: false });
      this.newItemText = "";
    },
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
  padding: 15px;
  text-align: center;
  color: white;
  font-size: large;
}

/**task display style */
#app .container-task {
  padding: auto 50px;
  width: 80%;
}


.ligne {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  padding: 20px;
}

#app .container-task .ligne .titre-colonne {
  font-weight: 800;
  font-size: large;
}

.colonne-2 {
  margin-right: 30px;
}

/**Task filtring style */
.container-filtre {
  background: gray;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
}

/**Style for adding tast */
/* .add.colonne-1{
  width: 50%;
} */
.input-task{
  border: solid dodgerblue 1px;
  height: 50px;
  width: 500px;
  font-size: larger;
  caret-color: blue;
}
.btn-add-task{
  color: white;
  background: dodgerblue;
  border-radius: 15px;
  padding: 20px;
}
</style>
