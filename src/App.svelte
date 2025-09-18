<script lang="ts">
    import ThemeSwitch from "./lib/ThemeSwitch.svelte";
</script>

<!-- ==========================================================================
     HEADER
     ========================================================================== -->
<header class="app-header">
    <a href="#" class="brand">
        <!-- Green Golden Humble Logo SVG -->
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="logo-icon">
            <path d="M12 2L2 7L12 12L22 7L12 2Z" stroke="var(--color-primary-glow)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M2 17L12 22L22 17" stroke="var(--color-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M2 12L12 17L22 12" stroke="var(--color-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        <h1>Web Editor</h1>
    </a>
    <div class="row">
        <button id="saveBtn" class="btn btn-secondary" title="Save work locally">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11l5 5v11a2 2 0 0 1-2 2z"></path><polyline points="17 21 17 13 7 13 7 21"></polyline><polyline points="7 3 7 8 15 8"></polyline></svg>
            <span>Save</span>
        </button>
        <button id="loadBtn" class="btn btn-secondary" title="Load from file">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="17 8 12 3 7 8"></polyline><line x1="12" y1="3" x2="12" y2="15"></line></svg>
            <span>Load</span>
        </button>
        <input id="openFile" type="file" accept="application/json" hidden>
        <ThemeSwitch />
    </div>
</header>

<!-- ==========================================================================
     MAIN CONTENT
     ========================================================================== -->
<main>
    <aside class="sidebar">
        <div class="card stack">
            <h2 class="card-header">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M15.5 3H5a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V8.5L15.5 3Z"></path><path d="M15 3v6h6"></path></svg>
                Task/Assignment
            </h2>
            <textarea id="assignment" class="text-input" placeholder="Describe the task for the student..."></textarea>
        </div>

        <div class="card stack">
            <label for="validationTest" class="card-header">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14.5 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V7.5L14.5 2z"></path><polyline points="14 2 14 8 20 8"></polyline><path d="m10 14-2 2 2 2"></path><path d="m14 18 2-2-2-2"></path></svg>
                Validation Test (JS)
            </label>
            <textarea id="validationTest" class="text-input" placeholder="Write tests to run against the solution..."></textarea>
            <div class="tip">
                Tip: <kbd class="kbd">Ctrl</kbd> + <kbd class="kbd">S</kbd> to save, <kbd class="kbd">Ctrl</kbd> + <kbd class="kbd">Enter</kbd> to run.
            </div>
        </div>

        <div class="card stack">
            <div class="row space-between">
                <h2 class="card-header">
                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="4 17 10 11 4 5"></polyline><line x1="12" y1="19" x2="20" y2="19"></line></svg>
                    Output
                </h2>
                <button class="btn btn-icon" title="Clear Output">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 4H8l-7 8 7 8h13a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2z"></path><line x1="18" y1="9" x2="12" y2="15"></line><line x1="12" y1="9" x2="18" y2="15"></line></svg>
                </button>
            </div>
            <div id="output" class="output-log" aria-live="polite"></div>
            <button class="btn btn-accent">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22c5.523 0 10-4.477 10-10S17.523 2 12 2 2 6.477 2 12s4.477 10 10 10z"></path><path d="m9 12 2 2 4-4"></path></svg>
                <span>Run with Tests</span>
            </button>
        </div>
    </aside>

    <section class="main-content">
        <div class="editor-panel">
            <div class="editor-header">
                <div aria-label="Code language tabs" class="tabs" id="webTabs" role="tablist">
                    <button class="tab active" role="tab" aria-selected="true" data-pane="html">HTML</button>
                    <button class="tab" role="tab" aria-selected="false" data-pane="css">CSS</button>
                    <button class="tab" role="tab" aria-selected="false" data-pane="js">JS</button>
                </div>
                <div class="row">
                    <button class="btn btn-secondary">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M2 12s3-7 10-7 10 7 10 7-3 7-10 7-10-7-10-7Z"></path><circle cx="12" cy="12" r="3"></circle></svg>
                        <span>Preview</span>
                    </button>
                    <button class="btn btn-primary" id="runWeb">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="5 3 19 12 5 21 5 3"></polygon></svg>
                        <span>Run</span>
                    </button>
                </div>
            </div>

            <div class="editor-container" data-pane="html">
                <textarea id="ed_html" class="editor" placeholder="HTML code goes here..."></textarea>
            </div>
            <div class="editor-container" data-pane="css" hidden>
                <textarea id="ed_css" class="editor" placeholder="CSS code goes here..."></textarea>
            </div>
            <div class="editor-container" data-pane="js" hidden>
                <textarea id="ed_js" class="editor" placeholder="JavaScript code goes here..."></textarea>
            </div>
        </div>

        <div class="card stack preview-panel">
            <h2 class="card-header">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="18" height="18" x="3" y="3" rx="2"></rect><path d="M21 12H3"></path><path d="M12 3v18"></path></svg>
                Live Preview
            </h2>
            <div class="preview-wrapper">
                <iframe id="preview" class="preview-frame" sandbox="allow-scripts allow-same-origin allow-modals allow-forms"></iframe>
            </div>
        </div>

        <footer class="footer">&copy;2025 IAFahim - All rights reserved.</footer>
    </section>
</main>