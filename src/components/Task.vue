<template>
	<div
		@dblclick="$emit('toggle-reminder', task.id)"
		:class="[task.reminder ? 'reminder' : '', 'task']"
	>
		<div v-if="!editing" class="task-content">
			<div>
				<h3 @dblclick="editing = true">{{ task.text }}</h3>
				<p>{{ task.day }}</p>
			</div>
			<div class="icons">
				<i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
				<i @click="editing = true" class="fas fa-edit"></i>
			</div>
		</div>
		<div v-if="editing" class="edit-task">
			<label for="edit-text">Text :</label>
			<input id="edit-text" type="text" v-model="editedTask.text" />
			<br />
			<label for="edit-day">Day :</label>
			<input id="edit-day" type="text" v-model="editedTask.day" />
			<br />
			<div class="buttons">
				<button @click="saveTask" class="save">Save</button>
				<button @click="cancelEdit" class="cancel">Cancel</button>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "Task",
	props: {
		task: Object,
	},
	data() {
		return {
			editing: false,
			editedTask: {
				id: this.task.id,
				text: this.task.text,
				day: this.task.day,
			},
		};
	},
	methods: {
		async saveTask() {
			this.$emit("update-task", this.editedTask);
			this.editing = false;
		},
		cancelEdit() {
			this.editing = false;
			this.editedTask = {
				id: this.task.id,
				text: this.task.text,
				day: this.task.day,
			};
		},
	},
};
</script>

<style scope>
.fa-times {
	color: red;
}

.fa-edit{
	color: green;
}

.task {
	background: #f4f4f4;
	margin: 5px;
	padding: 10px 20px;
	cursor: pointer;
}

.task-content {
	display: flex;
	justify-content: space-between;
}

.task.reminder {
	border-left: 5px solid green;
}

.icons {
	display: flex;
	flex-direction: column;
	justify-content: space-around;
}
.edit-task input {
	border: none;
	outline: none;
	font-size: 1rem;
	padding: 8px 5px;
	width: 80%;
	margin-bottom: 10px;
}
.edit-task label {
	font-size: 1rem;
	font-weight: bold;
	margin-right: 10px;
}
.edit-task button {
	margin-right: 10px;
}
.buttons {
	display: flex;
	justify-content: center;
}
.save {
	color: white;
	background-color: green;
	padding: 5px 10px;
	border: none;
	border-radius: 5px;
}
.cancel {
	color: white;
	background-color: red;
	padding: 5px 10px;
	border: none;
	border-radius: 5px;
}
</style>
