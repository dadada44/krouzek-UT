<script>
    // Stav pro toggle mobilního menu
    let isMenuOpen = false;
    $: {
    if (typeof window !== 'undefined') { // Ujisti se, že kód běží pouze na klientovi
      document.body.style.overflow = isMenuOpen ? 'hidden' : 'auto';
    }
  }

    // Navigační odkazy
    let links = [
      { name: "Domů", href: "/" },
      { name: "O nás", href: "/" },
      { name: "Login", href: "/login" },
      { name: "Profil", href: "/profile" },
    ];
</script>
<header>
    <div class="container">
      <!-- Hamburger Button -->
       <img src="/logo.png" alt="/" id="logo">

        <button
            class="hamburger"
            onclick={() => (isMenuOpen = !isMenuOpen)}
            aria-expanded={isMenuOpen}
            aria-label={isMenuOpen ? "Close menu" : "Open menu"}
        >
            <div class="line top" class:isOpen={isMenuOpen}></div>
            <div class="line middle" class:isOpen={isMenuOpen}></div>
            <div class="line bottom" class:isOpen={isMenuOpen}></div>
        </button>
    
      <!-- Navigační menu -->
        <div class="menu-overlay" class:isOpen={isMenuOpen}>
            <nav class="menu">
                {#each links as { name, href }}
                    <a href={href} onclick={() => (isMenuOpen = false)}>{name}</a>
                {/each}
            </nav>
        </div>
    </div>
</header>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');

header {
    background-color: #ffffff;
    height: 100px;
    margin: 0;
    padding: 0;
    width: 100%;
    display: flex;
    justify-content: center;
    box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;

    .container {
        max-width: 1300px;
        width: 100%;
        margin: auto;
        display: flex;
        justify-content: space-between;
        height: 100px;
        align-items: center;

        #logo {
            height: 70%;
            padding: 10px;
            padding-left: 3%;
            box-sizing: border-box;
            display: flex;
            justify-content: center;
            align-content: center;
        }

        .hamburger {
            display: none; /* Skryto pro větší obrazovky */
            flex-direction: column;
            gap: 6px;
            background: none;
            border: none;
            cursor: pointer;
            position: relative;
            z-index: 50;
            margin-right: 35px;

            .line {
                width: 35px;
                height: 3.5px;
                border-radius: 30px;
                background-color: #333;
                transition: all 0.8s cubic-bezier(0.23, 1, 0.32, 1);
            }
        }

        .menu {
            display: flex;
            gap: 2px; /* Mezera mezi odkazy */
            align-items: center;
            margin-right: 35px;
            z-index: 1000;

            a {
                margin: 15px;
                text-decoration: none;
                color: #007BFF;
                font-family: "Outfit";
                font-weight: 800;
                font-size: 25px;
                transition: all 0.3s ease;

                &:hover {
                    color: #4d7892;
                }
            }
        }
    }
}


    @media (max-width: 722px) { 
        .hamburger {
            display: flex !important;
            flex-direction: column;
            gap: 6px;
            background: none;
            border: none;
            cursor: pointer;
            position: relative;
            z-index: 50;
            margin-right: 35px;

        .line {
            width: 35px;
            height: 3.5px;
            border-radius: 30px;
            background-color: #333;
            transition: all 0.8s cubic-bezier(0.23, 1, 0.32, 1);

            &.top.isOpen {
                transform: translateY(9px) rotate(-120deg);
                background-color: #e1f1ff;
            }

            &.middle.isOpen {
                transform: scaleX(0);
                opacity: 0%;
            }

            &.bottom.isOpen {
                transform: translateY(-6px) translateX(-10px) rotate(-120deg);
            }

        }
        }

        .menu-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
       
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transform: scale(0.95);
            transition: transform 0.5s ease, opacity 0.5s ease;
            pointer-events: none;

            &.isOpen {
                opacity: 1;
                transform: scale(1);
                pointer-events: all;
                background-color: #4d7892;
                z-index: 10;
            }

            .menu {
                display: flex;
                flex-direction: column;
                gap: 1.5rem;
                text-align: center;
            

                a {
                color: #7f4343;
                font-size: 1.5rem;
                text-decoration: none;
                transition: all 0.3s ease;

                    &:hover {
                        color: #000000;
                    }
                }
            }
        }
    }

</style>
