<script>
    let menuOpen = false;

    function stopTouchScroll() {
    }

    function handleMenuClick() {
        let overflowY;
        if (!menuOpen) {
            window.scrollTo({ top: 0, behavior: "smooth" });
            document.addEventListener("touchmove", stopTouchScroll);
            overflowY = "hidden";
        } else {
            document.removeEventListener("touchmove", stopTouchScroll);
            overflowY = "auto";
        }
        menuOpen = !menuOpen;
        document.body.style.overflowY = overflowY;
    }
</script>

<div class="flex sm:hidden">
    <button
        id="burger"
        class="open-main-nav"
        class:is-open={menuOpen}
        on:click={handleMenuClick}
    >
        <span class="burger"></span>
    </button>
    <nav class="main-nav" id="main-nav" class:is-open={menuOpen}>
        <ul>
            <li>
                <a href="/">главная</a>
            </li>
            <li>
                <a href="/experience">опыт</a>
            </li>
            <li>
                <a href="/contact">контакты</a>
            </li>
        </ul>
    </nav>
</div>

<style>
    /* Main menu positionning */
    .main-nav {
        position: absolute;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        text-align: center;
        background: #202122;
        opacity: 0;
        z-index: -1;
        visibility: hidden;
        transition: all 0.375s;
    }

    .main-nav.is-open {
        opacity: 1;
        z-index: 100;
        visibility: visible;
    }

    /* Yellow band effect */
    .main-nav::before {
        content: "";
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background: #ffffff;
        transform-origin: 0 0;
        transform: skew(-14deg) translateX(-120%);
        transition: all 0.275s 0.1s;
    }

    .main-nav.is-open::before {
        transform: skew(-14deg) translateX(0);
    }

    /* Skewing effect on menu links */
    .main-nav ul {
        display: inline-flex;
        flex-direction: column;
        height: 100%;
        align-items: flex-end;
        justify-content: center;
        transform: translateX(-18%) skew(-16deg);
    }

    .main-nav li {
        display: block;
        margin: 0.5rem 0;
        text-align: right;
        transform: skew(16deg);
    }

    /* Apparition effect on links */
    .main-nav a {
        opacity: 0;
        transform: translateY(-10px);
    }

    .main-nav.is-open a {
        opacity: 1;
        transform: translateY(0);
    }
    .main-nav li:nth-child(1) a {
        transition: all 275ms 175ms;
    }
    .main-nav li:nth-child(2) a {
        transition: all 275ms 225ms;
    }
    .main-nav li:nth-child(3) a {
        transition: all 275ms 275ms;
    }
    .main-nav li:nth-child(4) a {
        transition: all 275ms 325ms;
    }
    .main-nav li:nth-child(5) a {
        transition: all 275ms 375ms;
    }

    /* Decoration */
    .main-nav ul,
    .main-nav li {
        list-style: none;
        padding: 0;
    }
    .main-nav a {
        display: block;
        padding: 12px 0;
        color: #000000;
        font-size: 1.4em;
        text-decoration: none;
        font-weight: bold;
    }

    .open-main-nav {
        z-index: 1000;
        padding: 10px 0;
        cursor: pointer;
    }
    .open-main-nav:focus {
        outline: none;
    }
    .burger {
        position: relative;
        display: block;
        width: 28px;
        height: 4px;
        margin: 0 auto;
        background: #6b6f72;
        transition: all 0.275s;
    }

    .burger:after,
    .burger:before {
        content: "";
        display: block;
        height: 100%;
        background: #6b6f72;
        transition: all 0.275s;
    }

    .burger:after {
        transform: translateY(-12px);
    }

    .burger:before {
        transform: translateY(8px);
    }

    /* Toggle State part */
    .is-open .burger {
        transform: skew(5deg) translateY(-8px) rotate(-45deg);
    }

    .is-open .burger:before {
        transform: translateY(0px) skew(-10deg) rotate(75deg);
    }

    .is-open .burger:after {
        transform: translateY(-12px) translateX(10px) skew(-20deg);
        opacity: 0;
    }
</style>
