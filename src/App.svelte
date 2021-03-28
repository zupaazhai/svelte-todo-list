<script>
    import Tailwind from './components/Tailwind.svelte'
    import TodoList from './components/TodoList.svelte'
</script>

<div id="app">
    <header class="bg-purple-500 p-3">
        <h1 class="text-white text-center">📝 Todo List + Svelte + Tailwind</h1>
    </header>
    <div class="max-w-md mx-auto">
        <TodoList />
    </div>
</div>