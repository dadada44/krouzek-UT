<script>
  import Header from "$lib/components/Header.svelte";
</script>

<body>
  <main>
    <div class="container">

      <div class="title">
        <h1>PROPOJUJEME UČITELE<br />SDÍLÍME ZNALOSTI!</h1>
      </div>

      <div class="content">
          <div class="text-content">
            <h1>*button component*</h1>
          </div>
          <div class="img-content">
            <img src="/libr.png" alt="" class="lib-img">
          </div>
      </div>
    </div>

    <div>

    </div>
  </main>
</body>


<style>

  main{
    background: url('/skola-background.png') no-repeat center center/cover;
    box-shadow: inset 0px -104px 43px -10px rgba(255,255,255,1);
  }
  
  .container {
      display: flex;
      flex-direction: column;
      position: relative;
      align-items: center;
      justify-content: center;
  }

  .content {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 100px;
      max-width: 1200px;
      width: 100%;
      padding: 20px;
      position: relative;
  }

  h1{
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fafafa;
    font-family: Outfit;
    font-size: 64px;
    font-weight: 800;
    text-align: end;


  }

  .img-content {
      display: flex;
      width: 200px;
      height: 400px;
      align-items: center;
      
  }

  .lib-img{
    width: 250px;
    height: 350px;
    box-shadow: 4px 4px 3px 1px #EF7800;
  }
</style>


