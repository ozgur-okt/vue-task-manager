<template>
	<AddTask v-show="showAddTask" @add-task="addTask" />
	<Tasks
		@toggle-reminder="toggleReminder"
		@delete-task="deleteTask"
    	@update-task="updateTask"
		:tasks="tasks"
	/>
</template>

<script>
import Tasks from "../components/Tasks";
import AddTask from "../components/AddTask";
import Task from "../components/Task"
export default {
	name: "Home",
	props: {
		showAddTask: Boolean,
	},
	components: {
		Tasks,
		AddTask,
    	Task
	},
	data() {
		return {
			tasks: [],
		};
	},
	methods: {
		async addTask(task) {
			const res = await fetch("api/tasks", {
				method: "POST",
				headers: {
					"Content-type": "application/json",
				},
				body: JSON.stringify(task),
			});
			const data = await res.json();
			this.tasks = [...this.tasks, data];
		},
		async updateTask(updatedTask) {
			const res = await fetch(`api/tasks/${updatedTask.id}`, {
				method: "PUT",
				headers: {
					"Content-type": "application/json",
				},
				body: JSON.stringify(updatedTask),
			});
			const data = await res.json();
      		this.tasks = this.tasks.map((task) =>
          	task.id === data.id ? { ...task, ...data } : task
        );
		},
		async deleteTask(id) {
			if (confirm("Are you sure?")) {
				const res = await fetch(`api/tasks/${id}`, {
					method: "DELETE",
				});

				res.status === 200
					? (this.tasks = this.tasks.filter((task) => task.id !== id))
					: alert("Error deleting task");
			}
		},
		async toggleReminder(id) {
			const taskToToggle = await this.fetchTask(id);
			const updTask = { ...taskToToggle, reminder: !taskToToggle.reminder };

			const res = await fetch(`api/tasks/${id}`, {
				method: "PUT",
				headers: {
					"Content-type": "application/json",
				},
				body: JSON.stringify(updTask),
			});

			const data = await res.json();

			this.tasks = this.tasks.map(
				(task) => task.id === id && { ...task, reminder: data.reminder }
			);
		},
		async fetchTasks() {
			const res = await fetch("api/tasks");

			const data = await res.json();

			return data;
		},
		async fetchTask(id) {
			const res = await fetch(`api/tasks/${id}`);

			const data = await res.json();

			return data;
		},
	},
	async created() {
		this.tasks = await this.fetchTasks();
	},
};
</script>
