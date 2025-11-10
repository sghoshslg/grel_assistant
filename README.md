# GREL Assistant v3.2 for OpenRefine 3.9
**GREL Assistant** is a helper plugin that makes writing GREL (General Refine Expression Language) code much easier inside OpenRefine’s transform dialogs.  
It provides an **always-visible floating button** to open a searchable library of ready-made GREL templates and inserts expressions directly into the transform editor.

Features

- Works with **OpenRefine 3.9+** (Butterfly module)
- Floating “GREL Helper” button** (bottom-right)
- Searchable templates** — quickly find common GREL operations
- Pre-built snippets** for text cleaning, regex, arrays, logic, and dates
 - One-click **Insert** into the Transform editor (auto-detects the last active dialog)
 Directory Structure

## Installation Steps

1. **Close OpenRefine** if running.
2. Unzip the downloaded file: grel-assistant-v3.2.zip
3. Copy the folder into your OpenRefine extensions directory.  
Typical paths: Windows: `C:\OpenRefine\extensions\grel-assistant\`, or `%APPDATA%\OpenRefine\extensions\grel-assistant\`, macOS/Linux: `~/openrefine/extensions/grel-assistant/`
4. Start OpenRefine again.
5. Open any project and look for:
- a badge at bottom-left: `GREL Assistant v3.2 loaded`
- a floating **“GREL Helper”** button at bottom-right.

## Usage

1. Open a project in OpenRefine.
2. Go to: Edit cells → Transform...
3. When the **Transform** dialog appears, click the **GREL Helper** button.
4. Use the **search bar** or scroll through grouped templates.
5. Adjust template parameters (like regex, separator, condition, etc.).
6. Click **Insert** to paste the generated GREL expression into the active editor.
7. Review and click **OK** to apply the transformation.

## Example Templates

| Category | Template | Resulting GREL Expression |
|-----------|-----------|----------------------------|
| Basics | Lowercase | `value.toLowercase()` |
| Cleaning | Collapse whitespace | `value.replace(/\s+/, " ").trim()` |
| Regex | Replace text via regex | `value.replace(/\s+/, "_")` |
| Dates | Extract year | `value.toDate().toString("yyyy")` |
| Logic | Blank to null | `if(isBlank(value), null, value)` |
| Special | Domain from URL | `value.parseUrl().host` |


## Troubleshooting
### No “GREL Helper” button visible?
- Make sure your folder is under the right `extensions/` path.
- Restart OpenRefine.
- Perform a **hard refresh** in your browser (`Ctrl + F5`).
- Type in console: window.grelAssistantLoaded
It should return true.

## Getting an “appendChild” error?
This version (v3.2) fixes that — it no longer tries to inject into headers.
If you still see it, clear browser cache and restart OpenRefine.

## Developer Notes
This plugin uses the Butterfly module system introduced in OpenRefine 3.6+.
It registers its JS and CSS using: ClientSideResourceManager.addPaths("project/scripts", module, [...]) and Safe DOM observation and insertion logic ensures compatibility with different browsers.

## License
MIT License
© 2025 Saptarshi Ghosh
