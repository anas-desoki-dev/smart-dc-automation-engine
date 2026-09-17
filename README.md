# Smart DC Automation & Cloud Sync Engine

An advanced desktop automation application engineered specifically for the construction industry to streamline Document Control (DC) and Quality Control (QC) workflows. This tool eliminates hours of manual data entry, file renaming, and cloud synchronization, replacing them with a robust, multithreaded Python engine.

## ⚠️ Repository Note
*This repository serves as a portfolio showcase of the architectural logic and UI/UX design. The proprietary Python source code is withheld to protect intellectual property.*

## 🚧 The Problem (Industry Pain Points)
In large-scale construction projects, Document Controllers struggle with:
1. **Unstructured Data:** Receiving hundreds of inconsistently named Excel submittals and inspection requests daily.
2. **Disguised Corruptions:** Third-party exported reports often come as HTML/CSV files disguised with `.xls` extensions, breaking standard data extraction pipelines.
3. **Manual Cloud Logging:** Uploading files to Google Drive, generating shareable links, and manually pasting them into massive Tracking Logs (Excel/Word) is highly prone to human error and consumes countless man-hours.

## 💡 The Solution & Core Features

### 1. Intelligent Cleaning & Formatting Pipeline
* **Smart Renaming:** Automatically scans deeply nested directories to extract specific markers, restructuring folder and file names based on strict engineering naming conventions (e.g., standardizing project cluster codes).
* **Auto-Healing Excel Engine:** Detects falsely disguised `.xls` files (HTML/CSV formats) and utilizes `pandas` to forcefully read, repair, and convert them into standard `.xlsx` files seamlessly in the background without user intervention.

### 2. Automated Submittal Extraction
* Reads mapped cells across hundreds of Excel files instantly.
* Utilizes customized Regex logic to deduce "Work Type" and "Stage" based on contextual keywords within the file descriptions (e.g., identifying "Final Plaster" or "Ventilation Shaft" from messy text strings).
* Compiles all extracted data into a single, unified `Smart_Report.xlsx` tracking log.

### 3. Threaded Cloud Synchronization (Google Drive API)
* Features a robust two-way sync capability (Folder-level and File-level) interacting directly with the Google Drive API.
* Safely checks for existing files via unique IDs, offering the user exact control (Replace/Skip/Cancel) to prevent duplicate uploads.
* **Auto-Generated Hyperlinked Logs:** Upon successful upload, it automatically generates an updated Excel report and a formal Microsoft Word document (`.docx`) where the document names act as direct clickable hyperlinks to the Google Drive files.

## 🛠 Tech Stack & Architecture
* **GUI Framework:** `customtkinter` for a responsive, modern Dark/Light mode interface.
* **Concurrency:** Implemented `threading` and `ThreadPoolExecutor` to handle heavy I/O operations (network uploads, bulk file reading) ensuring the UI remains highly responsive.
* **Data Processing:** `pandas`, `openpyxl`, and `python-docx` for complex Excel data manipulation and automated Word document generation.
* **Cloud Integration:** `google-api-python-client` with OAuth 2.0 authentication for secure file streaming to Google Workspace.
* **Text Processing:** Advanced `re` (Regex) module usage for dynamic string manipulation, bracket isolation, and intelligent capitalization of complex engineering acronyms.

## 📸 Interface Preview

![Main Dashboard](assets/main-dashboard.png)
*(Replace this link with your actual screenshot)*

