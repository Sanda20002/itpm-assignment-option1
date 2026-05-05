# ITPM Assignment 1 - Option 1: Test Automation for Singlish-to-Sinhala Chat Translator

## Project Overview

This project is a comprehensive **test automation framework** for validating a Singlish-to-Sinhala chat translator. Singlish refers to English text written using Sinhala script characters. The automation framework uses **Playwright** for browser-based testing and **openpyxl** for Excel test case management.

The framework is designed to:
- Automate the testing process of the chat translator application
- Execute test cases from an Excel spreadsheet
- Compare expected vs. actual output from the translator
- Generate detailed test reports with pass/fail status
- Handle edge cases and validate translation accuracy across diverse input types

## Test Coverage

### Test Cases: 50 Total
The test suite covers **24 different Singlish input types** with 50 comprehensive test cases, including:

- Basic word translations
- Phrase and sentence-level translations
- Special characters and punctuation handling
- Diacritic marks and tone indicators
- Mixed case inputs
- Whitespace and formatting variations
- Boundary conditions and edge cases
- Common user input patterns

### Test Results Summary
| Metric | Value |
|--------|-------|
| **Total Test Cases** | 50 |
| **Passed** | 0 |
| **Failed** | 50 |
| **Success Rate** | 0% |
| **Status** | In Progress |

## Technologies & Dependencies

### Core Technologies
- **Python 3.11+** - Primary programming language
- **Playwright** - Cross-browser automation framework for testing
- **Chromium** - Browser engine used for testing
- **openpyxl** - Excel file handling and result reporting
- **Microsoft Excel** - Test case specification format

### Python Dependencies
- `playwright` - Browser automation
- `openpyxl` - Excel spreadsheet manipulation

## Prerequisites

Before running the tests, ensure you have the following installed:

1. **Python 3.11 or higher**
   - Download from [python.org](https://www.python.org)
   - Verify installation: `python --version`

2. **Git** (optional, but recommended)
   - For version control and repository management

## Installation & Setup

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd itpm-assignment-option1
```

### Step 2: Install Python Dependencies
```bash
pip install -r requirements.txt
```

Or manually install the required packages:
```bash
pip install playwright openpyxl
```

### Step 3: Install Playwright Browsers
Playwright requires browser binaries to be installed:
```bash
playwright install chromium
```

Or install all supported browsers:
```bash
playwright install
```

### Step 4: Verify Installation
```bash
python test_automation.py --help
```

## How to Run the Tests

### Basic Usage
Run the tests with default settings:
```bash
python test_automation.py
```

### Command-Line Options

The test automation script supports various command-line arguments for customization:

```bash
python test_automation.py [OPTIONS]
```

#### Available Options:

| Option | Description | Default |
|--------|-------------|---------|
| `--url` | Target frontend URL to test | `https://www.pixelssuite.com/chat-translator` |
| `--excel` | Path to Excel test cases file | Auto-detected from workspace |
| `--sheet` | Sheet name in Excel file | ` Test cases` |
| `--input-col` | Input column name | Auto-detected (Singlish, Input, etc.) |
| `--expected-col` | Expected output column name | Auto-detected (Sinhala, Expected Output, etc.) |
| `--actual-col` | Actual output column name | `Actual output` |
| `--status-col` | Status column name | `Status` |
| `--header-row` | Header row number | Auto-detected |
| `--output` | Output Excel file path | Same as input file |
| `--wait-ms` | Wait time for translation (ms) | `5000` |
| `--retries` | Number of retry attempts | `8` |
| `--retry-wait-ms` | Wait time between retries (ms) | `1000` |
| `--type-delay-ms` | Delay between keystrokes (ms) | `30` |
| `--timeout-ms` | Playwright timeout (ms) | `60000` |
| `--headless` | Run browser in headless mode | Off (shows browser UI) |
| `--slow-mo-ms` | Slow motion delay (ms) | `0` |

### Example: Run with Custom Settings
```bash
python test_automation.py --url https://example.com/translator --headless --wait-ms 3000
```

### Example: Run with Custom Excel File
```bash
python test_automation.py --excel ./custom_test_cases.xlsx --output ./results.xlsx
```

## Project Structure

```
itpm-assignment-option1/
├── README.md                              # Project documentation (this file)
├── test_automation.py                     # Main test automation script
├── Assignment 1 - Test cases.xlsx         # Excel file with test cases & results
└── .git/                                  # Git version control directory
```

## File Descriptions

### `test_automation.py`
Main automation script that:
- Reads test cases from Excel file
- Launches Chromium browser using Playwright
- Navigates to the target translator URL
- Inputs Singlish text and captures output
- Compares expected vs. actual translation
- Records pass/fail status in Excel
- Generates detailed test report

**Key Features:**
- Smart column detection for flexible Excel formats
- Retry mechanism for handling timing issues
- Overlay dismissal (cookie banners, popups)
- Both chat and form-based translator support
- UTF-8 encoding support for Sinhala script

### `Assignment 1 - Test cases.xlsx`
Excel spreadsheet containing:
- **Column 1 (Singlish):** Singlish input text to be tested
- **Column 2 (Sinhala):** Expected translation in Sinhala script
- **Column 3 (Actual output):** Actual output from translator (auto-filled by script)
- **Column 4 (Status):** Pass/Fail result (auto-filled by script)

## Test Execution Flow

1. **Initialization**
   - Load test cases from Excel file
   - Parse command-line arguments
   - Validate input parameters

2. **Browser Launch**
   - Launch Chromium browser
   - Navigate to translator URL
   - Wait for page to load and stabilize

3. **For Each Test Case**
   - Dismiss any overlays (popups, cookies)
   - Clear input field
   - Type Singlish input with specified delay
   - Wait for translation to complete
   - Capture actual output
   - Compare with expected output
   - Record pass/fail status

4. **Completion**
   - Save results to Excel file
   - Display summary statistics
   - Close browser

## Troubleshooting

### Common Issues

#### Issue: Browser fails to launch
**Solution:** Ensure Playwright browsers are installed
```bash
playwright install chromium
```

#### Issue: Tests timeout waiting for translation
**Solution:** Increase wait time
```bash
python test_automation.py --wait-ms 10000
```

#### Issue: Column names not detected
**Solution:** Explicitly specify column names
```bash
python test_automation.py --input-col "Singlish" --expected-col "Sinhala"
```

#### Issue: Can't find Excel file
**Solution:** Specify full path to Excel file
```bash
python test_automation.py --excel C:\path\to\test_cases.xlsx
```

## Current Status

### Test Execution Results
- **Total Test Cases Executed:** 50
- **Passed:** 0
- **Failed:** 50
- **Status:** All tests currently failing - under investigation

### Next Steps
- [ ] Analyze test failures and root causes
- [ ] Identify translator bugs or issues
- [ ] Document failure patterns
- [ ] Suggest improvements to translator
- [ ] Retest after fixes applied

## System Requirements

| Requirement | Minimum | Recommended |
|-------------|---------|-------------|
| **OS** | Windows 7+ / macOS 10.13+ / Linux | Windows 10+ / macOS 11+ / Ubuntu 18.04+ |
| **Python** | 3.9 | 3.11+ |
| **RAM** | 2 GB | 4 GB+ |
| **Disk Space** | 500 MB | 1 GB+ |
| **Network** | Required | Required |

## Author Information

- **Registration Number:** IT23801318
- **Course:** ITPM (IT Project Management)
- **Assignment:** Assignment 1 - Option 1
- **Submission Date:** 2026-05-05

## License

This project is part of an academic assignment for ITPM course. Use is restricted to educational purposes.

## Support & Contact

For issues, questions, or improvements, please refer to the project documentation or contact the course instructor.