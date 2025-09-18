<script lang="ts">
    console.log("alert")
</script>

<header>
    <div class="container row">
        <div class="brand">
            <div class="logo"></div>
            <h1 class="title">Code Editor</h1>
        </div>
        <div class="row">
            <button id="saveBtn" class="btn secondary" title="Save work locally">
                <span>Save</span>
            </button>
            <button id="loadBtn" class="btn secondary" title="Load from file">
                <span>Load</span>
            </button>
            <input id="openFile" type="file" accept="application/json" hidden>
        </div>
    </div>
</header>

<main>
    <aside class="card panel stack">
        <h2>Task/Assignment</h2>
        <textarea id="assigment" class="text" placeholder="Write the text description ..."></textarea>

        <div class="stack">
            <label for="textArea">Validation test (JavaScript only - optional)</label>
            <textarea id="textArea" class="text"
                      placeholder="Write simple tests to append after the students code to see the solution"></textarea>
            <div class="muted">
                Tip:
                <span class="kbd">Ctrl</span> + <span class="kbd">S</span> to save,
                <span class="kbd">Ctrl</span> + <span class="kbd">Enter</span> to run.
            </div>
        </div>
    </aside>

    <section class="stack" id="web-only">
        <div id="webEditors" class="stack panel card">
            <div class="row`">
                <h2>Html/CSS/JS</h2>
                <button class="btn ok" id="runWeb">Run</button>
                <button class="btn ok" id="Open Preview">Preview</button>
            </div>
        </div>

        <div aria-label="web editors" class="tabs" id="webTabs" role="tablist">
            <button class="tab active" role="tab" aria-selected="true" tabindex="0" data-pane="html">HTML</button>
            <button class="tab" role="tab" aria-selected="false" tabindex="-1" data-pane="css">CSS</button>
            <button class="tab" role="tab" aria-selected="false" tabindex="-2" data-pane="js">JS</button>
        </div>

        <div class="editor-wrap" data-pane="html">
            <div id="ed_html" class="editor"></div>
        </div>


        <div class="editor-wrap" data-pane="css" hidden>
            <div id="ed_css" class="editor"></div>
        </div>

        <div class="editor-wrap" data-pane="js" hidden>
            <div id="ed_js" class="editor"></div>
        </div>

        <div class="stack" >
            <h3>Preview</h3>
            <iframe id="preview" class="preview" sandbox="allow-scripts allow-same-origin allow-modals allow-forms"></iframe>
        </div>
    </section>

    <aside class="card panel stack">
        <h2>Output</h2>
        <div id="output" class="out" aria-live="polite"></div>
        <div class="row">
            <button class="warn">Run with tests</button>
            <button class="btn secondary">Clear log</button>
        </div>
        <h3>Notes</h3>
        <ul class="muted">
            <il>Everything runs inside the browser in a sandbox.</il>
            <il>You can save the file as Json file and restore it...</il>
        </ul>
    </aside>
</main>
<div class="footer">&copy;2025 IAFahim - All rights reserved.</div>
