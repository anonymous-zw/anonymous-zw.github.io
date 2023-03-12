<script>
    import image from "./image.jpg";
    import ArrowDown from "svelte-material-icons/ArrowDown.svelte";
    import { onMount } from "svelte";

    onMount(() => {
        document.querySelectorAll(".letter").forEach((e, i) => {
            e.style.setProperty("--x", i);
        });
    });

</script>

<div class="section">
    <div class="wrapper">
        <div class="cover" style="background-image: url({image})">
            <div class="tint">
                
            </div>
            <h1 class="heading">
                {#each "Anonymous Clothing".split(" ").join(" ") as n}
                    <span class='letter'>{n}</span>
                {/each}
            </h1>
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

    .heading .letter {
        --x: 0;
        display: inline-block;
        line-height: 1em;
        transform: translateY(-100px);
        animation: appear 1s ease-in-out calc(0.034s * var(--x)) forwards;
    }

    .section, .wrapper, .cover {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .section {
        padding: 0;
        margin: 0;
        width: 100vw;
        height: 100vh;
        animation: shrink 1s ease-out forwards;
    }

    .cover {
        width: 100%;
        height: 100%;
        filter: grayscale(0.6);
        background-size: cover;
        background-position: center;
        border-radius: 0;
        animation: reveal 1s ease-out forwards;
        isolation: isolate;
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
        width: 100%;
        height: 100%;
        overflow: hidden;
        isolation: isolate;
        animation: smooth 1s ease-out forwards;
    }

    @keyframes appear {
        to {
            transform: translateY(0px);
        }
    }

    @keyframes smooth {
        to {
            border-radius: 1.5em;
        }
    }

    @keyframes shrink {
        to {
            padding: 2em;
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