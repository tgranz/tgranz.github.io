<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>JS Console Page</title>
  <style>
    body {
      margin: 0;
      font-family: system-ui, sans-serif;
      background: #111;
      color: #eee;
      display: flex;
      flex-direction: column;
      height: 100vh;
    }
    header {
      padding: 8px 12px;
      background: #222;
      border-bottom: 1px solid #333;
      font-size: 14px;
    }
    #location-info {
      font-size: 12px;
      color: #ccc;
      word-break: break-all;
    }
    main {
      display: flex;
      flex-direction: column;
      padding: 8px;
      gap: 8px;
      flex: 1;
    }
    #input-area {
      display: flex;
      flex-direction: column;
      gap: 4px;
    }
    #code-input {
      width: 100%;
      height: 120px;
      background: #000;
      color: #0f0;
      border: 1px solid #444;
      padding: 6px;
      font-family: "SF Mono", Menlo, Consolas, monospace;
      font-size: 13px;
      resize: vertical;
    }
    #controls {
      display: flex;
      gap: 8px;
      align-items: center;
    }
    button {
      padding: 6px 12px;
      border: 1px solid #555;
      background: #333;
      color: #eee;
      cursor: pointer;
      font-size: 13px;
    }
    button:hover {
      background: #444;
    }
    #single-line-input {
      flex: 1;
      background: #000;
      color: #0f0;
      border: 1px solid #444;
      padding: 4px 6px;
      font-family: "SF Mono", Menlo, Consolas, monospace;
      font-size: 13px;
    }
    #console-output {
      flex: 1;
      background: #000;
      color: #eee;
      border: 1px solid #444;
      padding: 6px;
      font-family: "SF Mono", Menlo, Consolas, monospace;
      font-size: 13px;
      overflow-y: auto;
      white-space: pre-wrap;
    }
    .log-line {
      margin: 0;
    }
    .log-time {
      color: #888;
    }
    .log-type {
      color: #0af;
    }
    .log-error {
      color: #f55;
    }
  </style>
</head>
<body>
  <header>
    <div><strong>JS Console Page</strong></div>
    <div id="location-info"></div>
  </header>

  <main>
    <section id="input-area">
      <label for="code-input">Multiline JS (Shift+Enter for newline, Enter to run):</label>
      <textarea id="code-input" spellcheck="false"></textarea>

      <div id="controls">
        <button id="run-code">Run multiline</button>
        <input
          id="single-line-input"
          type="text"
          placeholder="Single-line JS (press Enter to run)"
          spellcheck="false"
        />
        <button id="clear-output">Clear output</button>
      </div>
    </section>

    <section>
      <div>Console output:</div>
      <div id="console-output"></div>
    </section>
  </main>

  <script>
    (function () {
      const locationInfoEl = document.getElementById("location-info");
      const codeInputEl = document.getElementById("code-input");
      const singleLineInputEl = document.getElementById("single-line-input");
      const runCodeBtn = document.getElementById("run-code");
      const clearOutputBtn = document.getElementById("clear-output");
      const consoleOutputEl = document.getElementById("console-output");

      // Show URL and query params
      function showLocationInfo() {
        const href = window.location.href;
        const search = window.location.search;
        const params = new URLSearchParams(search);
        const entries = [];
        for (const [key, value] of params.entries()) {
          entries.push(key + "=" + value);
        }
        const queryString = entries.length ? entries.join("&") : "(none)";
        locationInfoEl.textContent =
          "href: " + href + " | query: " + queryString;
      }

      showLocationInfo();

      // Logging helpers
      function appendLog(type, value, isError) {
        const line = document.createElement("div");
        line.className = "log-line";

        const time = new Date().toLocaleTimeString();
        const timeSpan = document.createElement("span");
        timeSpan.className = "log-time";
        timeSpan.textContent = "[" + time + "] ";

        const typeSpan = document.createElement("span");
        typeSpan.className = isError ? "log-error" : "log-type";
        typeSpan.textContent = type + ": ";

        const valueSpan = document.createElement("span");
        try {
          if (typeof value === "object") {
            valueSpan.textContent = JSON.stringify(value, null, 2);
          } else {
            valueSpan.textContent = String(value);
          }
        } catch (e) {
          valueSpan.textContent = String(value);
        }

        line.appendChild(timeSpan);
        line.appendChild(typeSpan);
        line.appendChild(valueSpan);
        consoleOutputEl.appendChild(line);
        consoleOutputEl.scrollTop = consoleOutputEl.scrollHeight;
      }

      // Hook console.log / error / warn
      const originalConsole = {
        log: console.log,
        error: console.error,
        warn: console.warn,
        info: console.info,
      };

      console.log = function (...args) {
        originalConsole.log.apply(console, args);
        args.forEach((a) => appendLog("log", a, false));
      };
      console.error = function (...args) {
        originalConsole.error.apply(console, args);
        args.forEach((a) => appendLog("error", a, true));
      };
      console.warn = function (...args) {
        originalConsole.warn.apply(console, args);
        args.forEach((a) => appendLog("warn", a, false));
      };
      console.info = function (...args) {
        originalConsole.info.apply(console, args);
        args.forEach((a) => appendLog("info", a, false));
      };

      // Evaluate code safely-ish (still uses eval, so treat as trusted)
      function runCode(source, label) {
        if (!source.trim()) return;
        appendLog("input", source, false);
        try {
          const result = eval(source);
          if (typeof result !== "undefined") {
            appendLog("result", result, false);
          }
        } catch (err) {
          appendLog("throw", err, true);
        }
      }

      // Run multiline button
      runCodeBtn.addEventListener("click", function () {
        runCode(codeInputEl.value, "multiline");
      });

      // Multiline textarea: Enter to run, Shift+Enter for newline
      codeInputEl.addEventListener("keydown", function (e) {
        if (e.key === "Enter" && !e.shiftKey) {
          e.preventDefault();
          runCode(codeInputEl.value, "multiline");
        }
      });

      // Single-line input: Enter to run
      singleLineInputEl.addEventListener("keydown", function (e) {
        if (e.key === "Enter") {
          e.preventDefault();
          const src = singleLineInputEl.value;
          singleLineInputEl.value = "";
          runCode(src, "single-line");
        }
      });

      // Clear output
      clearOutputBtn.addEventListener("click", function () {
        consoleOutputEl.textContent = "";
      });

      // Some handy prefill example
      codeInputEl.value = `// Examples:
// window.location.href
// window.location.search
// new URLSearchParams(window.location.search).get("foo")
// console.log("Hello from device console");

console.log("href:", window.location.href);
console.log("search:", window.location.search);`;
    })();
  </script>
</body>
</html>
