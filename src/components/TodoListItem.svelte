<script>
    import { createEventDispatcher } from 'svelte'
    const dispatch = createEventDispatcher()

    export let todo = {}

    let style = {
        done: 'text-gray-200'
    }

    const toggleDone = () => {
        todo.isDone = !todo.isDone
        dispatch('toggle', { todo })
    }

    const remove = () => {
        dispatch('remove', { todo })
    }
</script>

<li class={ $$props.class + ' flex border border-gray-200 px-3 py-2 rounded mt-2' }>
    <div class="w-4/5">
        <span class={ todo.isDone ? style.done : '' }>{@html todo.message }</span>
    </div>
    <div class="w-1/5 text-right">
        <span>
            <a href on:click|preventDefault={ toggleDone }>✅</a>
        </span>
        <span>
            <a href on:click|preventDefault={ remove }>❌</a>
        </span>
    </div>
</li>