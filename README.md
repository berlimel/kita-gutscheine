# DATEV CSV Formatter for Kita Gutscheine

## Overview

This simple web tool converts CSV files containing Kita Gutscheine (childcare voucher) information into the DATEV import format. The entire process runs locally in your web browser, with no data sent to any server and no installation required.

## Features

- **Browser-Based:** Works completely offline in any modern web browser
- **Simple Interface:** Easy-to-use form with clear instructions
- **Local Processing:** All data stays on your computer
- **Automatic Formatting:** Handles the conversion to DATEV's required format
- **Error Handling:** Provides clear feedback if issues occur during processing

## Requirements

- Any modern web browser (Chrome, Firefox, Safari, Edge)
- A CSV file in the intermediate format with the following columns:
  - Name
  - Geb Dat
  - Kind-Nr./Antrag
  - Leist
  - Zeitraum
  - Tage
  - Entgelt
  - FEA
  - Fahrtkosten
  - Auszahlung

## Installation

No installation is needed. Simply download the `datev_formatter.html` file to your computer.

## Usage

1. Open the `datev_formatter.html` file in your web browser by double-clicking on it or right-clicking and selecting "Open with" your preferred browser.
2. Click "Select CSV file to convert" and choose your input CSV file.
3. Enter the month/year string in the format `-MM/YYYY` (e.g., `-10/2024` for October 2024).
4. Click the "Process and Download DATEV CSV" button.
5. Your browser will automatically download the converted `datev_import.csv` file.

## Output Format

The tool creates a CSV file with semicolon-separated values in the following format:

1. Betrag (Amount) - Taken from the "Auszahlung" column
2. WKZ (Currency) - Set to "EUR"
3. Soll_Haben (Debit/Credit) - Set to "H" (Credit/Haben)
4. Sachkonto (G/L Account) - Set to "8400"
5. Gegenkonto (Contra Account) - Set to "1200"
6. Belegdatum (Document Date) - Current date in DD.MM.YYYY format
7. Gutscheinnummer_Monat (Voucher Number with Month) - Combination of "Kind-Nr./Antrag" and the month/year string

## Technical Details

The tool includes:
- A custom CSV parser that handles quoted fields containing commas
- Data transformation according to DATEV requirements
- Automatic file generation and download functionality

## Troubleshooting

If you encounter issues:

1. **No download starts:** Check that you've selected a valid CSV file and entered the month/year string.
2. **Incorrect format in output:** Ensure your input CSV follows the expected format with the correct column order.
3. **Browser warning:** Some browsers may prompt you to allow downloads. Click "Allow" when asked.

## Customization

If you need to modify account numbers or other fixed values:

1. Open the `datev_formatter.html` file in a text editor.
2. Locate the section in the JavaScript code where the new row is created (around line 169).
3. Change the values such as '8400' (Sachkonto) or '1200' (Gegenkonto) as needed.
4. Save the file and use as normal.

## Data Privacy

This tool processes all data locally in your browser. No information is sent to any server, ensuring complete privacy and data security.

## License

This tool is provided as-is for internal use. You are free to modify it to suit your specific needs.
