<template>
<div>
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="#">Kanban App</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mr-auto">
            <!-- Logout Here -->
            <li class="nav-item">
                <a class="nav-link" href="" @click="logout">Log Out</a>
              </li>
              <!-- Logout -->
          </ul>
        </div>
      </nav>
  <div class="container-fluid pt-3">
        <h3>Kanban Board</h3>
        <button class="btn btn-primary" @click.prevent="toAdd" type="button">Add Task</button>
        <div class="row flex-row flex-sm-nowrap py-3">
            <Category
            v-for="(cat, i) in categories"
            :key = "i"
            :categor="cat"
            :tasks="tasks"
            @deleteTask="deleteTask"
            @changePage="changePage"
            @editTask="editTask"
            @toCategory="toCategory"
            @editCategory="editCategory"
            ></Category>
        </div>
    </div>
</div>
</template>

<script>
import Category from './Category'
export default {
    name: 'HomePage',
    components: {
        Category
    },
    props: ['tasks','categories'],
    methods : {
        logout(){
            localStorage.clear()
        },
        toAdd(){
            this.$emit('changePage', 'add-page')
        },
        deleteTask(id){
            this.$emit('deleteTask', id)
        },
        changePage(){
            this.$emit('changePage', 'edit-page')
        },
        editTask(obj){
            this.$emit("editTask",obj)
        },
        toCategory(obj){
            this.$emit('toCategory',obj)
        },
        editCategory(){
            this.$emit('editCategory', payload)
        }
    },
}
</script>

<style>

</style>