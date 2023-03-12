<script>
    import anime from 'animejs/lib/anime.es.js';
    import image from "./image.jpg";
    import ArrowDown from "svelte-material-icons/ArrowDown.svelte";
    import { onMount } from 'svelte';

    onMount(() => {
        anime.timeline({loop: false}).add({
            targets: '.heading .letter',
            translateY: [-100,0],
            easing: "easeOutExpo",
            duration: 1400,
            delay: (el, i) => 35 * i
        })
    });
</script>

<div class="section">
    <div class="wrapper">
        <div class="cover" style="background-image: url({image})">
            <div class="tint">
                
            </div>
            <h1 class="heading">{@html "Anonymous Clothing".replace(/\S/g, "<span class='letter'>$&</span>")}</h1>
            <div class="arrow">
                <ArrowDown color="#ffffff" size="36px" />
            </div>
        </div>
    </div>
</div>

<style>
    .arrow {
        position: fixed;
        bottom: 80px;
        opacity: 0;
        animation: arrow 1s ease-in forwards;
    }

    .heading {
        font-size: 2rem;
        font-weight: 500;
        color: #ffffff;
        text-transform: uppercase;
        letter-spacing: 0.4em;
        overflow: hidden;
        padding: 40px 0;
    }

    .section, .wrapper, .cover {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .section, .wrapper {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
        width: 100vw;
        height: 100vh;
    }

    .cover {
        width: 100%;
        height: 100%;
        filter: grayscale(0.6);
        background-size: cover;
        background-position: center;
        border-radius: 0;
        animation: reveal 1s ease-out forwards;
    }

    .tint {
        width: 100%;
        height: 100%;
        position: fixed;
        background-color: #33313400;
        animation: fade 1s ease-out infinite;
        animation-play-state: paused;
        animation-delay: calc(var(--scroll) * -2s);
        animation-iteration-count: 1;
        animation-fill-mode: both;
    }

    .wrapper {
        overflow: hidden;
        animation: grow 1s ease-out forwards;
    }

    @keyframes grow {
        to {
            width: calc(100vw - 4em);
            height: calc(100vh - 4em);
            border-radius: 1.5em;
        }
    }

    @keyframes reveal {
        to {
            transform: scale(1.1);
            filter: grayscale(0);
        }
    }

    @keyframes fade {
        to {
            background-color: #333134ff;
            backdrop-filter: blur(100px);
        }
    }

    @keyframes arrow {
        to {
            opacity: 1;
        }
    }
</style>