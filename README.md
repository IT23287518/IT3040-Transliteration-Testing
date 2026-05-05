# IT3040 Assignment 1 - Transliteration Accuracy Testing Automation

## Objective
This project automates the testing of the Singlish-to-Sinhala Chat Translator located at [PixelsSuite Chat Translator](https://www.pixelssuite.com/chat-translator). The script reads pre-defined Singlish test cases from an Excel file, automates the browser to input the text, waits for the translation, and automatically captures the actual Sinhala output. It then evaluates whether the test passed or failed by comparing the output against expected results.

## Automation Process Description
The core script (`test_automation.py`) performs the following automated steps:
1. **Reads Test Cases**: Loads `IT23287518_Test_cases.xlsx` using `openpyxl`.
2. **Browser Automation**: Launches a Chromium browser via `Playwright` and navigates to the Chat Translator.
3. **Test Execution**: For each row in the Excel sheet, the script:
   - Clears the translation input field (using `CTRL+A` and `Backspace`).
   - Inputs the Singlish test text.
   - Triggers the transliteration.
   - Waits dynamically for the output to generate or change.
4. **Result Recording**: Captures the generated Sinhala text and writes it back into the Excel file.
5. **Evaluation**: Automatically sets the test Status to `PASS` if the actual output matches the expected output, or `FAIL` otherwise.
6. **Persistence**: Saves the updated Excel file dynamically after processing each row.

## Tools & Technologies Used
* **Python**: Core programming language.
* **Playwright**: Framework for automated end-to-end testing in the browser.
* **Openpyxl**: Python library to read and dynamically write to Excel (`.xlsx`) files.

## Excel File Structure
The project depends on `IT23287518_Test_cases.xlsx` with specific columns:
* **Input**: The Singlish sentence or word to be tested.
* **Expected Output**: The correct Sinhala transliteration that the system is supposed to generate.
* **Actual Output** *(Auto-generated)*: The translated Sinhala text successfully captured by the automation script.
* **Status** *(Auto-generated)*: Automatically marked as `PASS` or `FAIL` based on the matching logic. 
> Note: The `Actual Output` and `Status` columns are written and overwritten automatically during the execution. 

## Installation

Ensure you have Python installed on your system.

1. Clone the repository:
```bash
git clone https://github.com/IT23287518/IT3040-Transliteration-Testing.git
cd test_automation
```

2. Create a virtual environment (optional but recommended):
```bash
python -m venv venv
# On Windows
venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate
```

3. Install the required dependencies:
```bash
pip install -r requirements.txt
```

4. Install the required Playwright browsers:
```bash
playwright install chromium
```

## How to Run the Project

To execute the test automation script, use the following exact command in your terminal:

```bash
python test_automation.py --excel "IT23287518_Test_cases.xlsx"
```

If you wish to run the script in visually hidden (headless) mode to run silently in the background:
```bash
python test_automation.py --excel "IT23287518_Test_cases.xlsx" --headless
```
