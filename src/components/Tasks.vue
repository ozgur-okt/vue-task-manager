<template>
  <div :key="task.id" v-for="task in tasks">
    <Task
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      @update-task="handleItemUpdated"
      :task="task"
    />
  </div>
</template>

<script>
import Task from './Task'

export default {
  name: 'Tasks',
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  methods: {
    handleItemUpdated(item) {
      this.$emit('update-task', item)
    },
  },
  emits: ['delete-task', 'toggle-reminder', 'update-task'],
}
</script>
