<script lang="ts">
    console.log("alert")
</script>

<header class="app-header">
    <a href="#" class="brand">
        <div class="logo"></div>
        <h1>Code Editor</h1>
    </a>
    <div class="row">
        <button id="saveBtn" class="btn btn-secondary" title="Save work locally">Save</button>
        <button id="loadBtn" class="btn btn-secondary" title="Load from file">Load</button>
        <input id="openFile" type="file" accept="application/json" hidden>
    </div>
</header>

<main>
    <aside class="sidebar">
        <div class="card stack">
            <h2>Task/Assignment</h2>
            <textarea id="assignment" class="text-input" placeholder="Write the text description..."></textarea>
        </div>

        <div class="card stack">
            <label for="validationTest">Validation Test (JS)</label>
            <textarea id="validationTest" class="text-input" placeholder="Write tests to run against the student's solution..."></textarea>
            <div style="font-size: 0.8rem; color: var(--text-secondary);">
                Tip: <kbd class="kbd">Ctrl</kbd> + <kbd class="kbd">S</kbd> to save, <kbd class="kbd">Ctrl</kbd> + <kbd class="kbd">Enter</kbd> to run.
            </div>
        </div>

        <div class="card stack">
            <div class="row space-between">
                <h2>Output</h2>
                <button class="btn btn-secondary" style="padding: 4px 8px; font-size: 0.75rem;">Clear</button>
            </div>
            <div id="output" class="output-log" aria-live="polite"></div>
            <button class="btn btn-warning">Run with Tests</button>
        </div>

        <div class="card stack">
            <h3>Notes</h3>
            <ul style="color: var(--text-secondary); font-size: 0.875rem; padding-left: var(--gap);">
                <li>Everything runs sandboxed in the browser.</li>
                <li>You can save and load your work as a JSON file.</li>
            </ul>
        </div>
    </aside>

    <section class="main-content">
        <div class="card" style="padding-bottom: 0;">
            <div class="row space-between flex-wrap">
                <div aria-label="Code language tabs" class="tabs" id="webTabs" role="tablist">
                    <button class="tab active" role="tab" aria-selected="true" data-pane="html">HTML</button>
                    <button class="tab" role="tab" aria-selected="false" data-pane="css">CSS</button>
                    <button class="tab" role="tab" aria-selected="false" data-pane="js">JS</button>
                </div>
                <div class="row" style="padding-bottom: var(--gap);">
                    <button class="btn btn-secondary">Preview</button>
                    <button class="btn btn-primary" id="runWeb">Run</button>
                </div>
            </div>
        </div>

        <!-- The actual editor instances will be mounted here -->
        <div class="editor-container" data-pane="html">
            <div id="ed_html" class="editor"></div>
        </div>
        <div class="editor-container" data-pane="css" hidden>
            <div id="ed_css" class="editor"></div>
        </div>
        <div class="editor-container" data-pane="js" hidden>
            <div id="ed_js" class="editor"></div>
        </div>

        <div class="card stack">
            <h2>Preview</h2>
            <div class="card" style="padding: 0; flex-grow: 1; overflow: hidden;">
                <iframe id="preview" class="preview-frame" sandbox="allow-scripts allow-same-origin allow-modals allow-forms"></iframe>
            </div>
        </div>

        <footer class="footer">&copy;2025 IAFahim - All rights reserved.</footer>
    </section>
</main>
