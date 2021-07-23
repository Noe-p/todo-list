<template>
  <div class="header">
    <h1>Todos</h1>
  </div>

  <div class="new-todo">
    <h2>Nouvelle note :</h2>
    <div class="new-todo-items">
      <div class="titre">
        <label for="titre">Titre</label>
        <input type="text" name="titre">
      </div>
      <div class="description">
        <label for="description">Description</label>
        <input type="text" name="description">
      </div>
    </div>
    <div class="ajouter">
       <input  @click="addTodo()" type="submit" value="Ajouter"/>
    </div>

  </div>

  <div>
    <div v-for="todo in todos" :key="todo.titre" class="todo" >
      <button></button>
      <div class="todo-item">
        <h2>{{ todo.titre }}</h2>
        <p>{{ todo.description }}</p>
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
      todos: []
    }
  },
  methods: {
    addTodo(){
      let titre = document.querySelector('input[name="titre"]').value;
      let description = document.querySelector('input[name="description"]').value;

      this.todos.unshift({
        titre: titre,
        description: description
      })
    }
  }
}

</script>

<style>
  .header{
    background-color: teal;
    margin:0;
    height: 200px;
    width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  h1{
    color: white;
    font-size: 5vw;
    font-family: 'Text-bold'
  }

  .new-todo{
    width: 70vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 50px;
  }

  .new-todo-items{
    display: flex;
  }

  .titre, .description{
    display: flex;
    flex-direction: column;
    margin-top: 30px;
  }

  .titre input, .description input{
    font-size: 1.5vw;
    font-family: 'Text';
    padding: 3px;
    margin: 10px;
    border-radius: 10px;
    border: solid 1px black;
  }

  .ajouter input{
    width: 120px;
    height: 40px;
    margin: 30px;
    background-color: white;
    box-shadow: none;
    border: solid 1px black;
    border-radius: 20px;
    font-size: 1.2vw;

    transition: all 0.2s;
  }

  .ajouter input:hover{
    cursor: pointer;
    background-color: teal;
    color: white;
    border: solid 1px white;
  }

  .todo{
    height: 150px;
    width: 80vw;
    display: flex;
    align-items: center;
    border-top: solid 1px black;
    text-align: left;
  }

  button{
    width: 50px;
    height: 50px;
    background-color: white;
    border: solid 1px black;
    border-radius: 50%;
    margin-right: 50px;
    position: relative;

    transition: all 0.2s;
  }


  button::after{
    display: block;
    content: '✓';
    position: absolute;

    font-size: 3em;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    opacity: 0;


    transition: all 0.2s;
    transition-delay: 0.3s;
  }

  button:hover{
    background-color: teal;
    cursor: pointer;
    border: solid 1px white;
  }

  button:hover::after {
    opacity: 1;
  }

  .todo-item{
    width: 75%;
  }

  h2{
    margin:0;
    height: 50px;
    display: flex;
    align-items: center;
  }

  p{
    max-height: 100px;
    overflow-y: scroll;
    margin: 0;
  }
</style>
