<template>
  <div class="header">
    <h1>Todos</h1>
  </div>

  <div class="new-todo">
    <h2>Nouvelle note :</h2>
    <div class="new-todo-items">
      <div class="titre">
        <label for="titre">Titre</label>
        <input type="text" name="titre" placeholder="Entrer un titre ici...">
      </div>
      <div class="description">
        <label for="description">Description</label>
        <input type="text" name="description" placeholder="Entrer une description ici...">
      </div>
    </div>
    <p class="alert"></p>
    <div class="ajouter">
       <input  @click="addTodo()" type="submit" value="Ajouter"/>
    </div>

  </div>

  <div v-for="todo in todos" :key="todo.titre" class="todo" >
    <button v-on:click="todoChecked(todo)" v-bind:class="{checked: todo.checked}"></button>
    <div class="todo-item">
      <h2>{{ todo.titre }}</h2>
      <p>{{ todo.description }}</p>
    </div>
    <div class="edit-item">
      <img @click="editItemOpen()" src="../assets/icons/edit.png" alt="edit"/>

      <img @click="rmTodo(todo)" src="../assets/icons/trash.png" alt="trash"/>
    </div>
    <div class="edit">
      <div @click="editItemClose()" class="editClose">✖</div>
      <h2>Éditer une note :</h2>
      <div class="titre">
        <label for="titre">Titre</label>
        <input type="text" name="titreEdit" :placeholder="[[ todo.titre ]]">
      </div>
      <div class="description">
        <label for="description">Description</label>
        <textarea type="text" cols="30" rows="5" name="descriptionEdit" :placeholder="[[ todo.description ]]"></textarea>
      </div>
      <p class="alertEdit"></p>
      <div class="ajouter">
         <input  @click="editTodo(todo)" type="submit" value="Ajouter"/>
      </div>
    </div>
  </div>


</template>

<script>

export default {
  name: 'Todos',
  components:{
  },
  data:() => {
    return {
      todos: [],
    }
  },

  methods: {
    addTodo(){
      let titre = document.querySelector('input[name="titre"]').value;
      let description = document.querySelector('input[name="description"]').value;
      let alert = document.querySelector('.alert');

      if(titre != ""){
        if(description != ""){
          this.todos.unshift({
            checked: 0,
            titre: titre,
            description: description
          });

          document.querySelector('input[name="titre"]').value = "";
          document.querySelector('input[name="description"]').value = "";
          alert.setAttribute("style", "color: rgb(45, 129, 41)");
          alert.textContent = "Todo ajoutée";

        } else {
          alert.setAttribute("style", "color: rgb(190, 16, 16)");
          alert.textContent = "Veuiller entrer une description..."
        }
      } else {
        alert.setAttribute("style", "color: rgb(190, 16, 16)");
        alert.textContent = "Veuiller entrer un titre..."
      }
    },
    todoChecked(todo){
      todo.checked = !todo.checked;
    },
    rmTodo(todo){
      this.todos.splice(this.todos.indexOf(todo),1);
    },
    editItemOpen(){
      let edit = document.querySelector('.edit');
      edit.classList.add('active');
    },
    editItemClose(){
      let edit = document.querySelector('.edit');
      edit.classList.remove('active');
    },
    editTodo(todo){
      let titre = document.querySelector('input[name="titreEdit"]').value;
      let description = document.querySelector('textarea[name="descriptionEdit"]').value;
      let alert = document.querySelector('.alertEdit');

      if(titre != ""){
        if(description != ""){
          this.todos.splice(this.todos.indexOf(todo),1,{
            checked: 0,
            titre: titre,
            description: description
          });
        } else {
          alert.setAttribute("style", "color: rgb(190, 16, 16)");
          alert.textContent = "Veuiller entrer une description..."
        }
      } else {
        alert.setAttribute("style", "color: rgb(190, 16, 16)");
        alert.textContent = "Veuiller entrer un titre..."
      }
    }

  }
}

</script>

<style src="../style/todos.css"></style>
