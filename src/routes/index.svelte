<script>
    import { onMount } from 'svelte';
    import divider from '../images/pattern-divider-desktop.svg';
    import dice from '../images/icon-dice.svg';
    const api_url = "https://api.adviceslip.com/advice";
    
    let quoteID = [];
    let quoteText = [];
    
    // use asynch/await to ensure that the data is received
    onMount(async () => {
        const response = await fetch(api_url);
        const data = await response.json();
        quoteID = data.slip.id;
        quoteText = data.slip.advice;
    });

    async function getQuote(){
        const response = await fetch(api_url);
        const data = await response.json();
        quoteID = data.slip.id;
        quoteText = data.slip.advice;
    }


</script>


<body>
    <div class="container">
        <script>console.log(quoteID);</script>
        <div class="quoteID">ADVICE #{quoteID} </div><!-- Advice ID goes here -->
        <br>
        <div class="quote">"{quoteText}"</div>
        <br>
        <img src={divider} alt="text and button divider">
        <div class="myButton">
            <button on:click={getQuote}>
                <img src={dice} alt="submit button" >
            </button>
        </div>
        

    </div>
    
    
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
      Coded by <a href=https://github.com/ssrivastava17>Stephanie Srivastava</a>.
    </div>
</body>

  <style>
    @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap');
    body{
        background-color: hsl(218, 23%, 16%);
        color: white;
        text-align: center;
        font-family: 'Manrope', sans-serif;
    }

    .container{
        background-color: hsl(217, 19%, 24%);
        margin: 100px auto;
        width: 450px;
        padding: 8%;
        border-radius: 25px;
        position: relative;
    }

    .quoteID {
        color:hsl(150, 100%, 66%);
        font-size: 14px;
    }
    .quote {
        font-size: 28px;
        margin: 10px auto;
        color: hsl(193, 38%, 86%);
    }

    .myButton{
        background-color: hsl(150, 100%, 66%);
        height: 40px;
        width: 40px;
        border-radius: 50%;
        align-items: center;
        margin: 5px auto;
        position: absolute;
        bottom: -25px;
        left: 46.5%
    }

    button{
        /* padding:0; */
        border: none;
        border-radius: 10px;
        /* background-color: hsl(150, 100%, 66%); */
        background-color: white;
    }
    .attribution { font-size: 11px; text-align: center; }
    .attribution a { color: hsl(228, 45%, 44%); }
  </style>