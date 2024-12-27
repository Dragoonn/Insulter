<script>
  
    let currentInsult = "";
  
    async function generateInsult() {
        try {
            const response = await fetch("https://insult.mattbas.org/api/insult", {
                method: "GET",
                mode: "cors",
            })

            if(response.ok) {
                const insult = await response.text()
                currentInsult = insult
            }
        } catch (err) {
            console.log(err)
        }
    }
</script>
  
<main>
    <div id="container">
        <h1>Insulter</h1>
        <p>{currentInsult}</p>
        <button on:click={generateInsult}>Make me feel bad</button>
    </div>
</main>
  
<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: 'Arial', sans-serif;
    }
  
    :global(body) {
        background: linear-gradient(to right, #141e30, #243b55);
        color: #ffffff;
    }
  
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        width: 100%;
    }
  
    #container {
        background-color: rgba(18, 18, 18, 0.9);
        border-radius: 12px;
        padding: 2rem;
        box-shadow: 0 4px 20px rgba(0,0,0,0.5);
        width: 90%;
        max-width: 600px;
        backdrop-filter: blur(10px);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
  
    h1 {
        color: #00ffcc;
        font-size: 2.5rem;
        margin-bottom: 1rem;
        text-align: center;
    }
  
    p {
        font-size: 1.25rem;
        margin-bottom: 1.5rem;
        line-height: 1.5;
        color: #00ffcc; 
    }
  
    button {
        padding: 0.75rem 1.5rem;
        font-size: 1rem;
        background-color: #00ffcc; 
        color: black; 
        border: none;
        border-radius: 6px;
        cursor: pointer;
        transition: background-color .3s ease, transform .2s ease;
        box-shadow: 0px 4px 15px rgba(0,255,204,.5);
    }
  
    button:hover {
        background-color: #00cc99; 
        box-shadow: 0px 6px 20px rgba(0,255,204,.7);
        transform: translateY(-2px) scale(1.05);
    }

    button:active {
      transform: translateY(0) scale(1);
      box-shadow: none;
    }
</style>
