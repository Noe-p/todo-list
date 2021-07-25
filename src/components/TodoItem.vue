<template>
  <div v-for="todo in todos" :key="todo.titre" class="todo" >
    <button></button>
    <div class="todo-item">
      <h2>{{ todo.titre }}</h2>
      <p>{{ todo.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
}
</script>

<style>
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
