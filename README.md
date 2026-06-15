# Local File Reader & Code Bundler

A high-performance, strictly browser-based utility designed to package entire codebases into a single, optimized text document. 

**The Core Application:** Preparing massive project context for Large Language Models (LLMs). This tool strips out token-wasting comments and whitespace, allowing you to feed maximum structural context into conversational AI models without hitting token limits or pasting files individually.

---

## Architectural Flow

The application processes user queries through a multi-stage Natural Language Processing pipeline before manipulating the virtual file staging area:

```text
      [User Natural Language Expression]
                      │
                      ▼
        ┌──────────────────────────┐
        │   Parenthesis Control    │ ──► Auto-balances unmatched brackets
        └──────────────────────────┘
                      │
                      ▼
        ┌──────────────────────────┐
        │  Token Protection Layer  │ ──► Insulates explicit text strings & paths
        └──────────────────────────┘
                      │
                      ▼
        ┌──────────────────────────┐
        │ Compromise.js Lemmatizer │ ──► Extracts semantic verb intent
        └──────────────────────────┘
                      │
                      ▼
        ┌──────────────────────────┐
        │   Recursive AST Parser   │ ──► Maps structural precedence (AND, OR, NOT)
        └──────────────────────────┘
                      │
       ┌──────────────┴──────────────┐
       ▼                             ▼
 [Intent: VIEW]             [Intent: KEEP/REMOVE]
       │                             │
       ▼                             ▼
Real-Time Filter UI         Batch Array Mutations
```
---

## Core Capabilities

| Feature | Description |
| :--- | :--- |
| **Zero Server Overhead** | Runs entirely in the browser environment utilizing the HTML5 File API. Data privacy is absolute; source code never touches an external server. |
| **Smart Ignore Pipeline** | Automatically circumvents common, high-volume dependency directories (node_modules, .git, dist, build). |
| **Granular Code Compression** | Employs configurable regex toggles to strip code comments, remove blank lines, and trim excess whitespace prior to compilation. |
| **Intelligent Flagging** | Scans file headers and payloads to automatically identify and badge binary contents or abnormally large files (>1.0 MB). |
| **AST NLP Engine** | Translates plain-English constraints into complex file-filtering actions, rendering a visual intent-mirroring UI before execution. |
| **Real-Time Metrics** | Calculates and displays the estimated combined output payload size dynamically as you manipulate the staging area. |

---

## Usage Guide

1. **Initialize:** Open the index.html file in any modern web browser. No local server environment is required.
2. **Stage:** Drag and drop your project directory into the designated drop zone.
3. **Filter:** Utilize the unified search interface to narrow down the files necessary for your target context (see Command Reference below).
4. **Optimize:** Select the required compression parameters via the interface checkboxes (Strip Comments, Remove Blank Lines, Trim Whitespace).
5. **Compile:** Assign a nomenclature to your payload and execute **Compile & Download**.
6. **Inject:** Upload the resulting structured .txt document directly to your preferred LLM.

---

## Command Reference

The primary input interface functions as a live string filter, a standard Command-Line Interface (CLI), and a Natural Language Processing (NLP) gateway.

### Advanced NLP Commands (ask:)
Prefix your input with "ask:" to route the query through the Compromise.js NLP engine and AST parser.

| Syntax Example | System Action |
| :--- | :--- |
| `ask: keep only .js files` | Isolates the staging area strictly to JavaScript files. |
| `ask: remove files over 50kb` | Sweeps the staging array for sizes exceeding the declared byte limit. |
| `ask: keep files inside src mentioning auth` | Processes a dual-constraint search based on path inclusion and string matches. |
| `ask: remove binary files` | Purges all non-plaintext objects flagged during the initial staging phase. |

### Standard CLI Execution (Press Enter)
Standard syntax patterns used for rapid, absolute batch actions.

| Command Syntax | Example | Execution |
| :--- | :--- | :--- |
| `.ext remove` | `.html remove` | Deletes all files sharing the specific extension from staging. |
| `keep .ext` | `keep .ts` | Wipes the entire staging area except objects matching the target extension. |
| `path/ remove` | `components/ remove` | Drops all nested files belonging to the declared directory. |
| `remove empty` | `remove empty` | Sweeps the array for files containing zero functional characters. |

### Live Visual Filtering (Instant)
Sub-commands that mutate the visual DOM representation without permanently mutating the underlying staging array.

| Filter Syntax | Example | Behavior |
| :--- | :--- | :--- |
| `String` | `config` | Renders only files containing "config" in the path or filename. |
| `-String` | `-mock` | Temporarily omits matching strings from the DOM list. |
| `>Size` | `>100kb` | Instantly isolates files evaluating true against the size operator. |

---

## System Limitations

* **Memory Constraints:** Processing happens entirely in-memory within the browser tab. Dragging monolithic, multi-gigabyte codebases directly into the drop zone may result in an Out of Memory browser crash. Best used on scoped microservices or specific sub-directories.
* **Binary Processing Limits:** The compiler is strictly designed for plaintext. While it intelligently flags binaries (images, PDFs, executables), attempting to force-compile them into the final .txt output will result in garbled encoding.
* **Regex Comment Stripping Constraints:** The comment removal tool relies on standard regex evaluations (targeting //, /* */, and ). It may occasionally misidentify complex string literals containing identical comment-like syntax.
* **Browser Compatibility:** Requires a modern browser (Chrome, Edge, Firefox, Safari) fully supporting the HTML5 File API and ES6+ JavaScript parameters. 

---

## Deployment

Because the architecture relies entirely on native browser APIs and external CDNs for CSS/NLP processing, this utility is completely decoupled from backend infrastructure. It can be hosted statically and instantly by uploading the index.html file to GitHub Pages, Vercel, or an AWS S3 bucket.
