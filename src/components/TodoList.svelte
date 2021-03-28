<script>
    import TodoForm from './TodoForm.svelte'
    import TodoListItem from './TodoListItem.svelte'
    import TodoList from './TodoListItem.svelte'

    let todos = [
        {
            message: 'Wake up 🥱',
            isDone: true
        },
        {
            message: 'Go to market 🥬',
            isDone: false
        }
    ]

    const onCreate = (newTodo) => {
        todos = [...todos, newTodo.detail]
    }

    const onToggle = (e) => {
        let todo = e.detail.todo
        todos[todo.id] = todo
    }

    const onRemove = (e) => {
        let todo = e.detail.todo
        todos.splice(todo.id, 1)
        todos = todos
    }
</script>

<div class="mt-4">
    {#if todos.length}
    <ul>
        {#each todos as todo, i (i)}
        <TodoListItem
            todo={ Object.assign({id: i}, todo) }
            on:toggle={ onToggle }
            on:remove={ onRemove } />
        {/each}
    </ul>
    {:else}
    <p class="text-gray-300 text-center">List is empty</p>
    {/if}
    <TodoForm on:create={ onCreate } />
</div>