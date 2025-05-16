# Google IT Automation Script Executor

A versatile Python utility designed to streamline IT file management through a simple, script-driven workflow.

## Overview

The Script Executor reads commands from a plain-text script, maps each line to an OO command object, runs them in sequence up to a configurable limit, and logs structured results for easy monitoring.

## Highlights

* **OO Command Classes**
  Each action—categorize, rename, move latest file, sort, list, delete, count—is its own class with a consistent `exe()` method. Extend or add new commands without touching the executor.

* **Configurable via JSON**
  All runtime settings (size thresholds, max commands, output type, log retention) live in `config.json`. Tweak behavior by editing JSON, not code.

* **Script-Driven Engine**
  Provide a script file (`-i commands.txt`), and the tool parses and executes commands automatically, generating logs and CSV reports in the `Output/` folder.

* **Easy CLI Use**
  Leverages `argparse` for clean `-i` (input) and `-o` (output) flags, making integration into shell scripts or cron jobs a breeze.

* **Robust Logging & Error Capture**
  Commands return structured status (state, message, command name). The executor logs pass/fail details with timestamps and writes optional CSV summaries for dashboards or audits.

* **Auto-Cleanup of Logs**
  Built-in retention logic prunes older logs based on the `Max_log_files` setting, keeping your workspace tidy.

* **Recursive Directory Operations**
  The `ListFiles` command traverses nested folders to catalog files and their parent directories—ideal for audits or inventories.

* **Smart File Sorting & Movement**
  Sort by name/date/size (asc/desc), and use `Mv_last` to automatically move the newest file to a target directory.

* **Cross-Platform Compatibility**
  Uses `os.path` and `pathlib` for reliable file handling on Windows, Linux, and macOS.

## Quick Start

```bash
python script_executor.py -i commands.txt -o execution.log
```

1. List commands in `commands.txt` (e.g., `Categorize /data 1024KB`, `Rename report.txt final.txt /data`).
2. Run the executor; check `execution.log` and `Output/` for detailed results.

---

## Why It Matters

* **Scalable**: Drop into larger automation pipelines or CI/CD.
* **Maintainable**: Configuration-driven, modular design.
* **Reliable**: Unified error handling and auto-prune logs ensure predictable operation.
* **Extensible**: Add, remove, or update commands with minimal effort.
