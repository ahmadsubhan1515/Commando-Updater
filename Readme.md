# Commando Paid Optimizer Auto Update System Requirements

Project Type: C# Windows Application (WinForms/WPF)

Goal:
Implement a fully automatic updater system for Commando Paid Optimizer.

## Update Workflow

When the application starts:

1. Check internet connection.
2. Download latest version information from:
   https://your-domain.com/version.json

Example:

{
"version": "1.0.1",
"download_url": "https://your-domain.com/Optimizer.zip",
"changelog": "Bug fixes and performance improvements"
}

3. Compare remote version with current application version.

4. If versions match:

   * Continue normal startup.

5. If a newer version exists:

   * Show update dialog.
   * Display current version.
   * Display latest version.
   * Display changelog.
   * Ask user to update.

6. If user accepts:

   * Download update ZIP file.
   * Show download progress bar.
   * Save ZIP in temporary folder.

7. Launch Updater.exe.

8. Main application must close completely.

9. Updater.exe should:

   * Wait until main application exits.
   * Backup existing files (optional).
   * Delete old application files.
   * Extract downloaded ZIP.
   * Replace all files.
   * Start updated Optimizer.exe.
   * Exit itself.

10. New version should launch automatically.

## Required Components

### Main Application

Create:

* UpdateManager.cs
* VersionChecker.cs
* DownloadManager.cs

Responsibilities:

VersionChecker:

* Download version.json
* Parse JSON
* Compare versions

DownloadManager:

* Download ZIP
* Report progress
* Handle errors

UpdateManager:

* Coordinate entire update process

### Updater Application

Create a separate project:

Updater.exe

Responsibilities:

* Receive ZIP path as command-line argument
* Wait for main application exit
* Replace files safely
* Extract ZIP
* Restart application

## Error Handling

Handle:

* No internet
* Invalid version.json
* Failed download
* Corrupted ZIP
* File access denied
* Missing files
* Extraction failure

Show user-friendly messages.

## Security Requirements

* Validate downloaded file exists.
* Validate ZIP before extraction.
* Only update from trusted URL.
* Prevent application crash during update.

## UI Requirements

Update Dialog:

Title:
"Warrior Optimizer Update Available"

Display:

Current Version:
Latest Version:
What's New:

Buttons:

[Update Now]
[Later]

Download Window:

* Progress Bar
* Download Speed
* Percentage
* Cancel Button

## Folder Structure

Application Folder:

/WarriorOptimizer
Optimizer.exe
Updater.exe
config.json
assets/
plugins/

Temporary Folder:

/Temp/WarriorUpdate
update.zip

## Development Requirements

Provide:

1. Complete source code.
2. File structure.
3. Required NuGet packages.
4. Installation instructions.
5. Build instructions.
6. Comments explaining every major function.
7. Example version.json.
8. Example update ZIP structure.

Use modern async/await patterns and proper exception handling.
