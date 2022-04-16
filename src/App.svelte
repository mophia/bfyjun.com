<script>
  let picPath = ["scenery.jpg", "fish.jpeg", "butterfly.jpeg"]

  let guest = ""
  let name = "BFY❤️JUN"
  const now = new Date()
  const start = new Date("08/10/2021")
  let Difference_In_Time = now.getTime() - start.getTime(); 
	var Difference_In_Days = Math.floor(Difference_In_Time / (1000 * 3600 * 24));

  let count= 0
  const IncrementCounter = () => {
    if (count + 1 >= picPath.length) {
      count = 0
    } else {
      count ++
    }
  }

  let events = [
    {id:0, name: "在一起", color:"pink", date:"2021-8-10", },
    {id:1, name: "250天纪念", color:"yellow", date:"2022-4-17", }
  ]

  const handleCardClick = (/** @type {{ id: any; name?: string; color: any; date?: string; }} */ info) => {
    document.getElementById(String(info.id)).style.backgroundColor=info.color
  }

  $: fullName = `${guest}君`

</script>

<main>
  <h1>{name}</h1>
  <h3 class="head">Hello {fullName}</h3>
  <h3 class="head">今天是布布和俊俊在一起的第{Difference_In_Days}天～～

  <div>
    <input type="text" bind:value={guest} placeholder="你是谁？">
    <button id="btn1" on:click={IncrementCounter}>❤️</button>
  </div>

  <br />

  <h3 class="head">重要的日子</h3>

    {#each events as event (event.id)}
      <div class="card" id={String(event.id)} on:click={() => handleCardClick(event)}>
      
        <h5>{event.name}</h5>
        <p>{event.date}</p>

      </div>
    {/each}



  

  <div style="margin-bottom: 60px;">
    <img src={picPath[count]} id="bg" alt="">
  </div>
  
</main>

<style>
  h1 {
   text-align: center;
  }
  .head {
   font-size: 28px;
   text-align: center;
  }

  #btn1 {
    font-size: 40px;
    text-align: center;
    width: 100px;
    height: 80px;
    background: transparent;
    border-color: transparent;
  }

  #btn1:hover {
    background-color: pink;
    transition: 0.7s;
  }

  input{
    outline-style: none ;
    border: 1px solid #ccc; 
    border-radius: 3px;
    padding: 13px 14px;
    width: 280px;
    font-size: 14px;
    font-weight: 700;
    font-family: "Microsoft soft";
  }

  input:focus{
    border-color: #66afe9;
    outline: 0;
    -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6);
    box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6)
  }

  .card {
    width: 400px;
    padding: 8px;
    border-radius: 20px;
    border: 2px solid grey;
    float: left;
    margin: 20px;
  }

  h5, p {
    margin: 4px 0px;
  }




</style>
