# Generate Yearly Reports - ACME System Automation

This repository contains an RPA project developed using UiPath to automate the process of generating and managing yearly reports for the ACME System. The automation logs into ACME System 1, reads work items, extracts relevant data, downloads reports, uploads the reports, and updates the work items with the upload ID.

## Libraries Used

This project uses the following custom libraries:

1. [**ACME System1 Website Library**](https://github.com/mnsy1/UiPath_ACMESystem1): Automates interactions with the ACME System1 website (web automation).

## 📖 Project Overview

This project automates the following steps:

### 1. **Initialization**
- Opens the ACME System1 website in the default browser.
- Reads configuration settings from the `Config.xlsx` file, including system URLs and login credentials asset.
- Initializes the queue for storing work items.

### 2. **Login to ACME System1**
- Log into the ACME System1 website using asset credentials.
- Verifies a successful login before proceeding.

### 3. **Get Transaction Data**
- Navigate to the Work Items page and extract all available work items.
- Each work item represents a transaction that will be processed through the subsequent steps.

### 4. **Process Transaction (REFramework)**

For each work item retrieved, the bot will:
   - The robot navigates to the report download page based on the extracted data.
   - Downloads the reports related to the extracted data for each vendor.

### 5. **Collect and Upload Reports**  
   - **Download Client Reports**: Gathers all downloaded reports for Vendor TaxId.
   - **Generate Yearly Report**: Consolidates reports into a yearly report.
   - **Upload Yearly Report**: uploads them, generating an Upload ID for each upload.
   - **Update Work Item**: Submits the Upload Confirmation ID and updates the work item status on the ACME System1 website.

### 5. **End Process**
- After all transactions are processed, the bot logs out of the ACME System1 website.
- The process gracefully ends, logging completion details.

### 6. **Exception Handling (REFramework)**

- Built-in error handling and retries for any failed transactions.
- Logs detailed error messages for debugging and troubleshooting.

## ✨ Features

- **Automated Data Extraction**: Reads and extracts all necessary data from the work items.
- **Automated Report Download**: Automates the process of navigating to the download page and downloading reports.
- **Report Upload and ID Generation**: Uploads reports and generates an upload ID for each.
- **Work Item Update**: Automatically updates work items with the upload ID and marks them as completed.
- **Secure Login**: Uses UiPath Orchestrator Assets for secure login management.

## 🛠️ Tech Stack

- **RPA Tool**: UiPath
- **Security**: Credentials stored in UiPath Orchestrator Assets
- **File Handling**: Automatically downloads and uploads files as part of the process

## Prerequisites

- **UiPath Studio** (latest version)
- **REFramework Template** preinstalled in UiPath Studio
- **Google Chrome** browser with UiPath extension
- **Valid ACME System1 account credentials**
- **Config.xlsx** file with system credentials asset, URLs, and queue information
