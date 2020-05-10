<script>
    let todos = [{
        name: "Buy milk",
        completed: false
    }, {
        name: "Buy car",
        completed: false
    }, {
        name: "Buy books",
        completed: false
    }];
    let originalList = [];

    $:completedCount = todos.filter(todo => todo.completed).length;
    $:str = `Completed ${completedCount} out of ${todos.length}`;

    const completeTodo = (index) => {
        todos = todos.map((todo, i) => {
            if(index === i) {
                todo.completed = !todo.completed;
            }
            return todo;
        });
    }

    const handleChange = (evt) => {
        //console.log(evt.target.checked);
        if(evt.target.checked) {
            originalList = todos;
            todos = todos.filter(todo => !todo.completed);
        } else {
            todos = originalList;
        }
    }
</script>

<main>
    <p>{str}</p>
    <div class="check-box">
        <input type="checkbox" on:change={handleChange}/>
        <label>Show Tasks Left</label>
    </div>
    <ul>
        {#each todos as todo, i} 
            <li class={todo.completed ? "done" : "notdone"} on:click={() => completeTodo(i)}>{todo.name}</li>
        {/each}
    </ul>
</main>

<style>
    .check-box {
        display: flex;
        margin-bottom: 10px;
    }
    label {
        margin-left: 10px;
    }
    ul {
        padding: 0;
        margin: 0;
        list-style: none;
        text-align: left;
    }
    li {
        font-size: 18px;
        padding: 10px;
    }
    .done {
        color: red;
        text-decoration: underline;
    }
    .notdone {
        color: green;
    }
</style>