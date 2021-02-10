<script>

  let todoData = {
    
  };

  let myTodos = []
  
  function handleSubmit() {
    console.log(todoData);

    myTodos = [...myTodos, {...todoData, created_at: new Date(), update_at: new Date()}]

    console.log(myTodos)
    // Clear the value
    todoData = {}
  }

  const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };

</script>

<style type="scss">
  .todo-page-container {
    display: flex;
    flex-direction: column;
    padding: 1rem;

    .todo-form {
      display: flex;
      padding: 0.6rem;

      .form-input { 
        margin-bottom: 10px;
        width: 100%;

        .form-control {
          padding: 10px;
          width: 100%;
          border-radius: 8px;
          border: 1px solid #cccc;
        }

        .btn-small {
          padding: 10px;
          display: flex;
          align-self: center;
          justify-content: center;
          border-radius: 8px;
          border: 1px solid #cccc;
        }
      }
    }

    .todo-list {
      display: flex;
      padding: 0.6rem;

      .container {
        width: 100%;
        .lists {
          border: 1px solid #cccc;
          border-radius: 8px;
          height: calc(100vh - 400px);
          width: 100%;
          padding: 10px;
          overflow-y: scroll;

          ul {
            list-style-type: none;
            padding: 10px;
          }

          h3 {
            font-weight: 800;
          }

          p {
            margin: 0;
          }

          .date {
            font-size: 10px;
            font-style: italic;
            color: #cccc;
            text-align: end;
            display: flex;
            justify-content: flex-end;
          }
        }
      }
    }
  }
</style>

<div class="todo-page-container">
  <div class='todo-form'>
    <form on:submit|preventDefault={handleSubmit}>
      <div class="form-input">
        <input 
          type="text"
          class="form-control"
          bind:value={todoData.title}
          placeholder="Title"
        />
      </div>
      <div class="form-input">
        <textarea 
          type="text"
          class="form-control"
          bind:value={todoData.descriptiom}
          placeholder="Description"
        />
      </div>
      <div class="form-input">
        <button class="btn-small">Submit</button>
      </div>
    </form>
  </div>
  <div class="todo-list">
    <div class="container">
      <h4>My Todos</h4>
      {#if myTodos.length > 0}
        <div class="lists">
          <ul>
            {#each myTodos as todo}
              <li>
                <h4>Title: {todo.title}</h4>
                <p>Descriptopn: {todo.descriptiom}</p>
                <span class="date">{new Intl.DateTimeFormat('en-US', options).format(todo.created_at)}</span>
              </li>
            {/each}
          </ul>
        </div>
      {:else}
        <p> No Task for the day</p>
      {/if }
    </div>
  </div>
</div>
