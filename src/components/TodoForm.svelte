<script>

    import { createEventDispatcher } from 'svelte'
    const dispatch = createEventDispatcher()

    const styles = {
        input: 'px-3 rounded-full py-2 border border-gray-200 w-full focus:outline-none focus:ring-2 focus:ring-purple-500',
        button: 'px-2 py-2 rounded-full bg-purple-500 text-white w-full',
        buttonDisabled: ' opacity-50'
    }

    let message = ''

    function save () {
        dispatch('create', { message })
        message = ''
    }
</script>

<form on:submit|preventDefault={ save } class="flex my-4">
    <div class="w-4/5">
        <div class="mr-2">
            <input bind:value={ message } type="text" class={ styles.input }>
        </div>
    </div>
    <div class="w-1/5">
        <button disabled={ !message.length } class={ styles.button + (!message.length ? styles.buttonDisabled : '') }>Add</button>
    </div>
</form>