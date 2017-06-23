<template>
  <div class="todo">
  	<div class="container col-sm col-offset-2">
		<h1>ToDo Task App</h1>
		<div class="panel panel-default">
			<h2 class="text-center">Add New Task</h2>
			<form @submit.prevent="addTask">
				<div class="col-sm-8">
					<input type="text" class="form-control" v-model="tasks.name">
				</div>
				<div class="col-sm-4">
					<input type="submit" class="btn btn-primary btn-block">
				</div>
			</form>
			&nbsp;
		</div>
		<table class="table">
			<thead>
				<th>Checkmark Done</th>
				<th>Task Name</th>
				<th>Delete</th>
			</thead>
			<tbody>
				<tr v-for="task in tasks">
					<td><input type="checkbox" v-model="task.done"></td>
					<td><span :class="{ taskDone: task.done }">{{ task.name }}</span></td>
					<td><button class="btn btn-danger btn-block" @click="deleteTask(task)">Delete</button></td>
				</tr>
			</tbody>
		</table>
  	</div>
  </div>
</template>

<script>
export default {
  name: 'todo',
  data () {
    return {
    	tasks: [
    		{name: 'Gotta do this task first', done: false}
    		,{name: 'Buy some pet food', done: false}
    		,{name: 'Install fish tank in living room', done: false}

    	]
    }
  }
  ,methods: {
  	addTask: function (e) {
  		this.tasks.push({
  			name: this.tasks.name
  			,done: false
  		});
  	}
  	,deleteTask: function (task) {
  		this.tasks.splice(this.tasks.indexOf(task),1)
  	}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.taskDone {
	text-decoration: line-through;
}
</style>
