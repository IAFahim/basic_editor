<script lang="ts">
    import { onMount } from "svelte";

    let isDarkMode = true;

    // On component mount, check the saved theme from localStorage
    onMount(() => {
        const savedTheme = localStorage.getItem("theme");
        if (savedTheme) {
            isDarkMode = savedTheme === "dark";
        } else {
            // If no theme is saved, use the system preference
            isDarkMode = window.matchMedia("(prefers-color-scheme: dark)").matches;
        }
        applyTheme();
    });

    // Toggle the theme
    function toggleTheme() {
        isDarkMode = !isDarkMode;
        applyTheme();
        localStorage.setItem("theme", isDarkMode ? "dark" : "light");
    }

    // Apply the theme to the body
    function applyTheme() {
        if (isDarkMode) {
            document.body.dataset.theme = "dark";
        } else {
            document.body.dataset.theme = "light";
        }
    }
</script>

<button on:click={toggleTheme} class="btn btn-icon theme-toggle" title="Toggle Theme">
    {#if isDarkMode}
        <!-- Moon Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
        </svg>
    {:else}
        <!-- Sun Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <circle cx="12" cy="12" r="5"></circle>
            <line x1="12" y1="1" x2="12" y2="3"></line>
            <line x1="12" y1="21" x2="12" y2="23"></line>
            <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
            <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
            <line x1="1" y1="12" x2="3" y2="12"></line>
            <line x1="21" y1="12" x2="23" y2="12"></line>
            <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
            <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
        </svg>
    {/if}
</button>

<style>
    .theme-toggle {
        /* Add any specific styling for the button if needed */
    }
</style>