<script>
  // 1. STATE: This is where we store our data.
  // 'todos' is an array of objects.
  let todos = [
    { id: 1, text: 'Learn Svelte basics', completed: true },
    { id: 2, text: 'Build a To-Do list', completed: false }
  ];

  // This variable holds the text currently typed in the input box.
  let newTaskText = '';

  // 2. FUNCTIONS: Actions that change our state.
  function addTask() {
    // Prevent adding empty tasks
    if (newTaskText.trim() === '') return;

    // Create a new task object
    const newTask = {
      id: Date.now(), // Unique ID based on current time
      text: newTaskText,
      completed: false
    };

    // Reactivity rule in Svelte: 
    // To update an array, we reassign it with the old items (...todos) plus the new one.
    todos = [...todos, newTask];
    
    // Clear the input box
    newTaskText = '';
  }

  function deleteTask(idToRemove) {
    // Filter out the task with the matching ID
    todos = todos.filter(todo => todo.id !== idToRemove);
  }

  function toggleComplete(idToToggle) {
    // Find the task and flip its 'completed' boolean
    todos = todos.map(todo => {
      if (todo.id === idToToggle) {
        return { ...todo, completed: !todo.completed };
      }
      return todo;
    });
  }
</script>

<main class="app-container">
  <div class="todo-card">
    <h1>My Tasks</h1>

    <!-- 3. INPUT FORM -->
    <form class="input-group" on:submit|preventDefault={addTask}>
      <!-- bind:value automatically keeps the input box and 'newTaskText' in sync -->
      <input 
        type="text" 
        placeholder="What needs to be done?" 
        bind:value={newTaskText}
      />
      <button type="submit">Add</button>
    </form>

    <!-- 4. LIST RENDERING -->
    <ul class="todo-list">
      <!-- We loop over the 'todos' array using #each -->
      {#each todos as todo (todo.id)}
        <li class="todo-item" class:completed={todo.completed}>
          
          <label class="task-label">
            <input 
              type="checkbox" 
              checked={todo.completed}
              on:change={() => toggleComplete(todo.id)}
            />
            <span class="task-text">{todo.text}</span>
          </label>

          <button class="delete-btn" on:click={() => deleteTask(todo.id)}>
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
              <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
              <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
            </svg>
          </button>
        </li>
      {/each}
    </ul>
    
    {#if todos.length === 0}
      <p class="empty-state">All caught up! ✨</p>
    {/if}
  </div>
</main>
