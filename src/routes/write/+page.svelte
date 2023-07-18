<script>
    import { goto } from "$app/navigation";

    let burning = false;

    async function burn() {
        setTimeout(() => goto("/"), 4000);
        burning = true;
    }
</script>

<svelte:head>
    <title>Fleeting Thoughts</title>
</svelte:head>
<div class="menu">FleetingThoughts</div>
<div class="container centered" class:burning>
    <h1>NEW NOTE:</h1>
    <br />
    <textarea class="text-area" />
    <button on:click={burn}>Burn</button>
</div>

<style>
    @keyframes burning-ani {
        0% {
            opacity: 100%;
            filter: blur(0);
        }
        100% {
            opacity: 0;
            filter: blur(1);
        }
    }

    .burning {
        animation: burning-ani 4s cubic-bezier(0.075, 0.82, 0.165, 1);
    }
    .text-area {
        background-color: var(--background-color-2);
        color: var(--text-colour);
        height: 40vh;
        width: 60vw;
        font-family: "Victor Mono", monospace;
        font-size: 1.5em;
    }

    button {
        color: var(--text-colour);
        background-color: var(--primary);
        border: none;
        border-radius: 2rem;
        text-transform: uppercase;
        margin-top: 1rem;
        height: 4rem;
        width: 7rem;
        font-size: 1.5rem;
    }

    button:hover,
    button:focus-within {
        background-color: var(--secondary);
        cursor: pointer;
    }

    .text-area:focus,
    .text-area:hover {
        outline: none;
        border-color: var(--primary);
    }
</style>
