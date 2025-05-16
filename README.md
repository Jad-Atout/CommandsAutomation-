# Learning Journey: Google IT Automation

A Python-based tool I built to automate everyday file management tasks and level up my scripting skills.

## Key Features

* **Modular Commands**: Each action (categorize, rename, sort, move latest, list, delete, count) lives in its own class with a simple `exe()` method.
* **JSON Configuration**: Control thresholds, max commands, output format, and log retention without changing code.
* **Script-Driven Workflow**: Read plain-text scripts of commands, parse them into objects, and execute sequentially for repeatable automation.
* **Robust Logging**: Structured pass/fail status with timestamps logged to files and optional CSV summaries for easy review.
* **Auto-Cleanup**: Built-in log retention cleans up old files automatically based on configurable limits.
* **Recursive Directory Ops**: Walk nested folders to list and catalog files for audits or reporting.
* **Smart File Sorting & Moving**: Sort files by name, date, or size—then move the newest file to a target directory.
* **CLI Integration**: Simple `-i`/`-o` flags via `argparse` to plug into scripts or cron jobs.
* **Cross-Platform Compatibility**: Uses `os.path` and `pathlib` for reliable operation on Windows, macOS, and Linux.

## Quick Start

1. Install Python 3.x (no extra dependencies).
2. Create a `config.json` to set your preferences (thresholds, limits, output type).
3. Write a script file (`commands.txt`), one command per line, e.g.:

   ```txt
   Categorize /data 1024KB
   Rename report.txt final.txt /data
   Mv_last /downloads /backup
   ```
4. Run:

   ```bash
   python script_executor.py -i commands.txt -o execution.log
   ```
5. Review `execution.log` and the `Output/` folder for results.

## Under the Hood

* **ScriptExecutor**: Reads config, parses command lines into objects, executes up to the set limit, and gathers results.
* **Command Classes**: Encapsulate single tasks with error handling and return structured status.
* **Logging & Reporting**: Uses Python’s `logging` for detailed logs and CSV writers for dashboards.
* **Cleanup Logic**: Counts existing log/output files and prunes oldest when exceeding limits.

## Why I Built It

This project was my hands‑on dive into:

* Designing modular, maintainable Python code
* Building config-driven automation pipelines
* Mastering file and directory and file manipulation in Python
* Crafting reliable logging and cleanup strategies

It reinforced best practices for real-world scripting and prepared me for larger automation challenges.
