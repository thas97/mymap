<template>
  <div>
    <h1>Sample page</h1>
    <NLink to="/">
      Top Page
    </NLink>
    <br>
    <NLink to="/about">
      About Page
    </NLink>
<div>
     <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-format-list-checkbox</v-icon>
          </v-list-item-action>
          <NLink to="/">
           Top Page
          </NLink>
          </v-list-item>
          
          <v-list-item link>
           
            <NLink to="/about">
      About Page
    </NLink>
           </v-list-item>
      </v-list>
      
    </v-navigation-drawer>
    <v-app-bar app color="indigo" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"/>
      <v-toolbar-title>To-do List</v-toolbar-title>
    </v-app-bar>
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col class="text-center">
            <v-list>
              <v-subheader>ToDo List</v-subheader>
              <v-text-field
                label="Title"
                v-model="todoTitle"
                @keyup.enter="addTodo"
              ></v-text-field>
              <!-- <v-list-item> -->
                <!-- <div> -->
                  <v-btn
                    class="ma-2"
                    color="green darken-1" dark
                    v-on:click="deleteCompleted(todo)"
                  >Archive
                    <v-icon>mdi-check-all</v-icon>
                  </v-btn>
                  <v-btn
                    class="ma-2"
                    color="red" dark
                    v-on:click="deleteAll(todo)"
                  >Clear
                    <v-icon>mdi-delete-forever</v-icon>
                  </v-btn>
                <!-- </div> -->
              <!-- </v-list-item> -->
              <v-list-item v-for="todo in todos" :key="todo.id">
                <v-list-item-action>
                  <v-checkbox
                    v-model="todo.completed"
                    @change="changeAllChecked()"
                  ></v-checkbox>
                </v-list-item-action>
                <!-- <v-list-item-action>
                  <v-btn
                    icon ripple
                    v-model="todo.completed"
                    v-on:click="deleteTodo(todo)"
                  ><v-icon>mdi-done-outline</v-icon>
                  </v-btn>
                </v-list-item-action> -->
                <v-list-item-content>
                  <v-text-field
                    v-if="todo.id == editTodoId"
                    label="Title"
                    v-model="editTodoTitle"
                    @keyup.enter="update(todo)"
                  ></v-text-field>
                  <v-list-item-title
                    v-else
                    v-on:dblclick="editTodo(todo)"
                    v-text="todo.title"
                    v-bind:class="{lineThrough: todo.completed}"
                  ></v-list-item-title>
                </v-list-item-content>
                <v-list-item-icon>
                  <v-btn
                    v-if="todo.completed"
                    icon ripple
                    v-on:click="deleteTodo(todo)"
                  ><v-icon>mdi-check</v-icon>
                  </v-btn>
                  <v-btn
                    v-else
                    icon ripple
                    v-on:click="deleteTodo(todo)"
                  ><v-icon>mdi-delete</v-icon>
                  </v-btn>
                </v-list-item-icon>
              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    <v-footer color="indigo" app>
      <span class="white--text">&copy; 2019</span>
    </v-footer>
   </v-app>
</div>
  </div>
</template>


 
 
 <script>
 export default {
  props: {
    source: String
  },
  data: () => ({
    todoId: 0,
    todoTitle: "",
    editTodoTitle: "",
    drawer: null,
    editTodoId: null,
    todos: []
  }),
  methods: {
    addTodo: function() {
      this.todos.push({
        id: this.todoId ++,
        title: this.todoTitle,
        completed: false
      });
      this.todoTitle = "";
    },
    deleteTodo: function(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    },
    editTodo: function(todo) {
      this.editTodoId = todo.id;
    },
    update: function(todo) {
      todo.title = this.editTodoTitle;
      this.editTodoTitle = "";
      this.editTodoId = null;
    },
    deleteAll: function() {
      this.todos.splice(0);
    },
    deleteCompleted: function(todo) {
      for (i=0;i<todo.id;i++) {
        pass;
      }
    },
    changeAllChecked: function() {
      if (this.todo.checked) {
        pass;
      } else {
        pass;
      }
    },
  },
};
// console.log(todos);
</script>
<style>
.lineThrough {
  text-decoration: line-through;
}
</style>