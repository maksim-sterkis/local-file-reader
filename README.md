# Local File Reader and Code Bundler

A fast, secure, and entirely client-side web utility designed to package entire codebases or batches of files into a single structured text document. This tool is optimized to prepare project context for Large Language Models (LLMs) while dramatically stripping out unnecessary token waste.

## Features

* **Zero Server Overhead:** Runs entirely in your browser. Your source code never leaves your local machine.
* **Smart Ignore List:** Automatically skips system and dependency folders like node_modules, .git, dist, and build when processing folders.
* **Granular Code Compression:** Choose to strip code comments, remove blank lines, or trim excess whitespace before generating the final output document.
* **Dynamic Warning Badges:** Automatically identifies binary files and flags individual files exceeding 1.0 MB with clean visual indicators.
* **Integrated CLI:** Execute advanced batch actions, size calculations, and negative filters directly from the built-in search bar.

## Search Bar and CLI Commands Reference

The main input bar acts as both a real-time visual filter and an execution prompt.

### Live Filtering (Instant View Update)
* **Text Search:** Type any keyword or partial file name to show only matching paths.
* **Negative Filter:** Type a minus sign or exclamation mark before a word (e.g., `-test` or `!mock`) to temporarily hide matching files from the visual list.
* **Size Filter:** Type comparison operators (e.g., `>100kb` or `<5kb`) to instantly isolate specific file sizes in the list view.

### Execution Commands (Type and Press Enter)
* **Remove Specific Extension:** Type `.ext remove` or `.ext r` (e.g., `.html remove`) to delete all matching files from the staging area.
* **Keep Only Specific Extension:** Type `keep .ext` or `.ext keep` (e.g., `keep .js`) to wipe out every staged file except those matching the target extension.
* **Nuke Subdirectories:** Type `path/ remove` or `remove path/` (e.g., `components/ui/ remove`) to instantly drop a specific nested folder.
* **Purge Empty Files:** Type `remove empty` or `empty remove` to sweep out ghost files or blank placeholders.
* **Clear Registry Flags:** Type `remove binary` or `remove large` to clear targeted warning groups from your staging area in bulk.

## Deployment

This project is fully optimized for static hosting solutions like GitHub Pages. Because it relies entirely on local browser APIs, Tailwind CDN, and client-side processing, you can deploy it instantly by naming the file index.html and uploading it to a public GitHub repository.
