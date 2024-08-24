<script>
  import { createEventDispatcher } from "svelte";

    let selected =  10 

    const dispatch = createEventDispatcher()

    const onChange = (e) => {
        selected = e.currentTarget.value
        dispatch('rating-select', selected)
        console.log(e.currentTarget.value)
    }
</script>

<!-- <ul class="rating">
    <li>
        <input type="radio" id="num1" name="rating" value="1" on:change={onChange} checked={selected === 1}>
        <label for="num1">1</label>
    </li>
    <li>
        <input type="radio" id="num2" name="rating" value="2" on:change={onChange} checked={selected === 2}>
        <label for="num1">2</label>
    </li>
    <li>
        <input type="radio" id="num3" name="rating" value="3" on:change={onChange} checked={selected === 3}>
        <label for="num1">3</label>
    </li>
    <li>
        <input type="radio" id="num4" name="rating" value="4" on:change={onChange} checked={selected === 4}>
        <label for="num1">4</label>
    </li>
    <li>
        <input type="radio" id="num5" name="rating" value="5" on:change={onChange} checked={selected === 5}>
        <label for="num1">5</label>
    </li>
    <li>
        <input type="radio" id="num6" name="rating" value="6" on:change={onChange} checked={selected === 6}>
        <label for="num1">6</label>
    </li>
    <li>
        <input type="radio" id="num7" name="rating" value="7" on:change={onChange} checked={selected === 7}>
        <label for="num1">7</label>
    </li>
    <li>
        <input type="radio" id="num8" name="rating" value="8" on:change={onChange} checked={selected === 8}>
        <label for="num1">8</label>
    </li>
    <li>
        <input type="radio" id="num9" name="rating" value="9" on:change={onChange} checked={selected === 9}>
        <label for="num1">9</label>
    </li>
    <li>
        <input type="radio" id="num10" name="rating" value="10" on:change={onChange} checked={selected === 10}>
        <label for="num1">10</label>
    </li>
</ul> -->

<ul class="rating">
    {#each Array(10) as _, i}
      <li>
        <input
          type="radio"
          id={`num${i + 1}`}
          name="rating"
          value={i + 1}
          on:change={onChange}
          checked={selected === i + 1}
        />
        <label for={`num${i + 1}`}>{i + 1}</label>
      </li>
    {/each}
  </ul>
  

<style>
    .rating {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin: 30px 0;
    }

    .rating li {
        position: relative;
        background: #f4f4f4;
        width: 50px;
        height: 50px;
        padding: 10px;
        text-align: center; 
        border-radius: 50%;
        font-size: 19px;
        border: 1 #eee solid;
        transition: 0.3s;
    }

    .rating li label {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 50px;
        height: 50px;
        padding: 10px;
        border-radius: 50%;
        transform: translate(-50%, -50%);
        cursor: pointer;
    }

    .rating li:hover {
        background: #ff6a95;
        color: #fff;
    }

    /* Make actual radio select inisible */
    [type='radio']{
        opacity: 0;
    }

    /* Use vibling select */
    [type='radio']:checked + label {
        background: #ff6a95;
        color: #fff;
    }
</style>