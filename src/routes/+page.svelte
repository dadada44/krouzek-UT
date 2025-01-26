<script>
  import Button from "$lib/components/Button.svelte";

  import { text } from 'drizzle-orm/sqlite-core';
  import { onMount } from "svelte";
  import AOS from "aos";
  import "aos/dist/aos.css";

  onMount(() => {
    AOS.init({
      duration: 900,
      easing: "ease-in-out",
      once: true,
    });
  });
</script>

<body>
  <main>
    <div class="container">
      <div class="title" data-aos="fade-up">
        <h1>PROPOJUJEME UČITELE<br />SDÍLÍME ZNALOSTI!</h1>
      </div>

      <div class="content" 
        data-aos="fade-zoom-in"
        data-aos-easing="ease-in-back"
        data-aos-delay="300"
        data-aos-offset="0">
        
        <div class="text-content">
          <h2>Naším cílem je vytvořit prostor, kde mohou pedagogové sdílet své zkušenosti, 
              materiály a nápady pro inspiraci a podporu vzdělávání.</h2>
            <button Button>Hi</button>

        </div>

        <div class="img-content">
          <img src="/libr.png" alt="Kniha v knihovně" class="lib-img" />
        </div>
      </div>
    </div>
  </main>
</body>

<style>
  main {
    background: url('/skola-background.png') no-repeat center center/cover;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
    padding-top: 100px;
    gap: 40px;
  }

  .title {
    text-align: center;
  }

  h1 {
    color: #fafafa;
    font-family: 'Outfit', sans-serif;
    font-size: 64px;
    font-weight: 800;
    line-height: 1.2;
    margin: 0;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  }

  .content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 30%;
    max-width: 900px;
    width: 100%;
    padding: 20px;
  }

  .text-content {
    flex: 1;
    text-align: left;
  }

  .text-content h2 {
    color: #ffffff;
    font-family: 'Outfit', sans-serif;
    margin: 0;
    font-family: Outfit;
    font-size: 32px;
    font-weight: 800;
    line-height: 40.32px;
    text-align: left;
  }

  h2{
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  }

  .img-content {
    flex: 0 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .lib-img {
    width: 250px;
    height: auto;
    box-shadow: rgba(239, 119, 0, 0.779) 7px 7px;
  }

  @media (max-width: 768px) {
    .content {
      flex-direction: column;
      gap: 35px;
      text-align: center;
    }

    .text-content {
      text-align: center;
    }

    .lib-img {
      width: 220px;
    }

    h1 {
      font-size: 48px;
    }
  }
</style>
