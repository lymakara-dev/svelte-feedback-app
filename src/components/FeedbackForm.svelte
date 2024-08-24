<script>
    import {v4 as uuidv4} from 'uuid';
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import RatingSelect from "./RatingSelect.svelte";
  import { createEventDispatcher } from 'svelte';

  let text = ''
  let rating = 10
  let btnDisable = true
  let min = 10
  let message

  const dispatch = createEventDispatcher()
  
  const handleSelect = (e) => rating = e.detail

  const handleInput = () => {
    if(text.trim().length <= min){
        message = `Text must be at least ${min} charaters`
        btnDisable = true
    }else{
        message = null
        btnDisable = false
    }
  }

  const handleSubmit = () => {
    if(text.trim().length > min){
        const newFeedback = {
            id: uuidv4(),
            text,
            rating: +rating
        }
        dispatch('add-feedback',newFeedback)
    }
  }
</script>

<Card>
    <header>
        <h2>How would you rate your service with us?</h2>
    </header>
    <form on:submit|preventDefault={handleSubmit}>
        <!-- Rating section -->
         <RatingSelect on:rating-select={handleSelect}/>
         <div class="input-group">
            <input type="text" on:input={handleInput} bind:value={text} placeholder="Tell us something that keeps you coming back">
            <Button disabled={btnDisable} type="submit">Send</Button>
        </div>
        {#if message}
            <div class="message">
                {message}
            </div>
        {/if}
    </form>
</Card>

<style>
    header {
        max-width: 400px;
        margin: auto;
        text-align: center;
    }

    .input-group {
        display: flex;
        flex-direction: row;
        border: 1px #ccc solid;
        padding: 8px 10px;
        border-radius: 8px;
        margin: 15px;
    }

    input {
        flex-grow: 2;
        border: none;
        font-size: 16px;
    }

    input:focus {
        outline: none;
    }

    .message {
        padding-top: 10px;
        text-align: center;
        color: purple;
    }
</style>
