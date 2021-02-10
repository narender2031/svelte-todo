<script>

  let todoData = {
    
  };

  let myTodos = []
  
  function handleSubmit() {
    console.log(todoData);

    myTodos.push({...todoData, created_at: new Date(), update_at: new Date()})
    // Clear the value
    todoData = {}
  }

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
    
  </div>
</div>