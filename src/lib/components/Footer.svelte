<div>
    <footer>
        <div class="footer-container">
            <div class="footer-logo">
                <img src="/logo.png" alt="">
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean finibus eu dui id feugiat.</p>
            </div>
            <div class="footer-column">
                <h4>Lorem ipsum</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
            </div>
            <div class="footer-column">
                <h4>Lorem ipsum</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
            </div>
            <div class="footer-column">
                <h4>Lorem ipsum</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
            </div>
        </div>
        <div class="footer-bottom">
            <p>Team Script <span class="email-icon">✉️</span></p>
        </div>
    </footer>
</div>

<style>
    footer {
        background-color: #222;
        border-top: 5px solid #ff8000;
        padding: 20px;
        color: white;
        z-index: 10;
    }

    .footer-container {
        display: flex;
        justify-content: space-around;
        align-items: flex-start;
        gap: 20px;
        flex-wrap: wrap;
    }

    .footer-logo img {
        max-width: 100%;
        height: auto;
    }

    .footer-column, .footer-logo {
        text-align: left;
        color: #fff;
        flex: 1;
        min-width: 200px;
    }

    .footer-bottom {
        text-align: center;
        margin-top: 20px;
        font-size: 0.9em;
        color: #ccc;
    }

    @media (max-width: 768px) {
        .footer-container {
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .footer-logo, .footer-column {
            flex: none;
            width: 100%;
            margin-bottom: 20px;
        }

        .footer-bottom {
            font-size: 0.8em;
        }
    }
</style>
