<script>
    import divider from '../images/pattern-divider-desktop.svg';
    import dice from '../images/icon-dice.svg';
    const api_url = "https://api.adviceslip.com/advice";
    var quoteID = 1;
    var quoteText = "Testing";
    
    async function getQuote(){
        // console.log("Clicked!")
        const response = await fetch(api_url);
        const data = await response.json();
        console.log(data);
        console.log(data.slip.id)
        console.log(data.slip.advice);
        quoteID = data.slip.id;
        quoteText = data.slip.advice;
    }

</script>


<body>
    <div class="container">
        <span style="color:hsl(150, 100%, 66%);">Advice {quoteID} </span><!-- Advice ID goes here -->
        <br>
        "{quoteText}"
        <br>
        <img src={divider} alt="text and button divider">
        <br>
        <button on:click={getQuote} style="padding:0; border: none;">
            <img src={dice} alt="submit button" >
        </button>

    </div>
    
    
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
      Coded by <a href=https://github.com/ssrivastava17>Stephanie Srivastava</a>.
    </div>
</body>

  <style>
    body{
        background-color: hsl(217, 19%, 24%);
        color: white;
        text-align: center;
    }

    .container{
        background-color: hsl(217, 19%, 38%);
    }

    .attribution { font-size: 11px; text-align: center; }
    .attribution a { color: hsl(228, 45%, 44%); }
  </style>