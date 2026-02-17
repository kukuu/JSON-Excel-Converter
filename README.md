# J2E 

JSON Excel Converter. Scalable and modular script that accepts input/output paths as terminal arguments. **Please use with acknowledgement.** Visit:

- AZZOTTO Movies, https://www.azzottomovies.com/: **Free Streaming Service**.
  - _Features_:
    - https://www.azzottomovies.com/movie/434853
    - https://www.azzottomovies.com/lounge
    - JUKEBOX: Selection of GenXZ music
    - Global Music and Sports Events 2026
    - Pletora of GallerIES and Trends

- SPYDER
A Net Zero initiative, SPYDER uses  AI-driven analytics and user-friendly compute engine tools to compare tariffs, track consumption, simulate scenarios, predict outcomes, enable forecasting, facilitate predictive maintenance, and recommend cost-effective renewable energy options by saving on energy bills. It integrates dynamic carbon footprint tracking, personalised energy-saving strategies, and compliance frameworks into a scalable platform - helping users align sustainability goals with practical, measurable actions. Its proven track record is honed in applying AI to core business problems. SPYDER uses Machine Learning, Artificial Intelligence, Large Language Models and Retrieve Augmentation Generators algorithms to interpret complex energy tariffs, automating a manual consultancy process and enabling customers to self-serve the best pricing, thereby solving a direct business and customer challenge.

  - 1. https://github.com/kukuu/SPYDER/blob/main/spyder-overview.md
    2. 2. https://www.energytariffscheck.com/

```

#!/usr/bin/env node

/**
 * Universal JSON ↔ Excel Converter
 * 
 * Usage:
 *   node convert-json-excel.js json-to-excel <input-json> <output-excel>
 *   node convert-json-excel.js excel-to-json <input-excel> <output-json>
 * 
 * Examples:
 *   node convert-json-excel.js json-to-excel public/data/cycling-ads/cycling-ads.json public/data/spreadsheets/cycling-ads/cycling-ads.xlsx
 *   node convert-json-excel.js excel-to-json public/data/spreadsheets/cycling-ads/cycling-ads.xlsx public/data/cycling-ads/cycling-ads.json
 */

const fs = require('fs');
const path = require('path');
const XLSX = require('xlsx');

// ============================================
// UTILITY FUNCTIONS
// ============================================

/**
 * Ensure directory exists
 */
function ensureDirectoryExists(filePath) {
  const dirname = path.dirname(filePath);
  if (fs.existsSync(dirname)) {
    return true;
  }
  ensureDirectoryExists(dirname);
  fs.mkdirSync(dirname, { recursive: true });
  return true;
}

/**
 * Show help message
 */
function showHelp() {
  console.log(`
📊 Universal JSON ↔ Excel Converter

Usage:
  node convert-json-excel.js json-to-excel <input-json> <output-excel>
  node convert-json-excel.js excel-to-json <input-excel> <output-json>
  node convert-json-excel.js help

Examples:
  # Convert JSON to Excel
  node convert-json-excel.js json-to-excel ./data.json ./output.xlsx
  
  # Convert Excel to JSON  
  node convert-json-excel.js excel-to-json ./data.xlsx ./output.json

  # Use with your specific paths
  node convert-json-excel.js json-to-excel public/data/cycling-ads/cycling-ads.json public/data/spreadsheets/cycling-ads/cycling-ads.xlsx
  
Arguments:
  <input-json>   Path to input JSON file
  <output-excel> Path where Excel file will be saved
  <input-excel>  Path to input Excel file  
  <output-json>  Path where JSON file will be saved

Notes:
  - Directories will be created automatically if they don't exist
  - JSON files are formatted with 2-space indentation
  - Excel sheets auto-size columns for better readability
  `);
}

/**
 * Convert JSON to Excel
 */
function convertJsonToExcel(inputPath, outputPath) {
  console.log('🔄 Converting JSON to Excel...');
  console.log(`   Input: ${inputPath}`);
  console.log(`   Output: ${outputPath}`);

  try {
    // Check if input file exists
    if (!fs.existsSync(inputPath)) {
      console.error(`❌ Input file not found: ${inputPath}`);
      return false;
    }

    // Read JSON file
    const jsonData = JSON.parse(fs.readFileSync(inputPath, 'utf8'));
    console.log(`✅ Read ${jsonData.length} records from JSON`);

    // Create worksheet
    const worksheet = XLSX.utils.json_to_sheet(jsonData);

    // Auto-size columns for better readability
    const range = XLSX.utils.decode_range(worksheet['!ref']);
    const columns = [];
    for (let C = range.s.c; C <= range.e.c; ++C) {
      let maxWidth = 10; // minimum width
      for (let R = range.s.r; R <= range.e.r; ++R) {
        const cell = worksheet[XLSX.utils.encode_cell({ r: R, c: C })];
        if (cell && cell.v) {
          const width = String(cell.v).length + 2;
          if (width > maxWidth) maxWidth = Math.min(width, 50); // cap at 50
        }
      }
      columns.push({ wch: maxWidth });
    }
    worksheet['!cols'] = columns;

    // Create workbook
    const workbook = XLSX.utils.book_new();
    XLSX.utils.book_append_sheet(workbook, worksheet, 'Sheet1');

    // Ensure output directory exists
    ensureDirectoryExists(outputPath);

    // Write Excel file
    XLSX.writeFile(workbook, outputPath);
    console.log(`✅ Excel file created: ${outputPath}`);
    console.log(`   Size: ${(fs.statSync(outputPath).size / 1024).toFixed(2)} KB`);

    return true;
  } catch (error) {
    console.error('❌ Error converting JSON to Excel:', error.message);
    return false;
  }
}

/**
 * Convert Excel to JSON
 */
function convertExcelToJson(inputPath, outputPath) {
  console.log('🔄 Converting Excel to JSON...');
  console.log(`   Input: ${inputPath}`);
  console.log(`   Output: ${outputPath}`);

  try {
    // Check if input file exists
    if (!fs.existsSync(inputPath)) {
      console.error(`❌ Input file not found: ${inputPath}`);
      return false;
    }

    // Read Excel file
    const workbook = XLSX.readFile(inputPath);
    const sheetName = workbook.SheetNames[0];
    const worksheet = workbook.Sheets[sheetName];

    // Convert to JSON
    const jsonData = XLSX.utils.sheet_to_json(worksheet);
    console.log(`✅ Read ${jsonData.length} records from Excel`);

    // Ensure output directory exists
    ensureDirectoryExists(outputPath);

    // Write JSON file with pretty formatting
    fs.writeFileSync(
      outputPath,
      JSON.stringify(jsonData, null, 2),
      'utf8'
    );
    console.log(`✅ JSON file created: ${outputPath}`);
    console.log(`   Size: ${(fs.statSync(outputPath).size / 1024).toFixed(2)} KB`);

    return true;
  } catch (error) {
    console.error('❌ Error converting Excel to JSON:', error.message);
    return false;
  }
}

// ============================================
// MAIN SCRIPT EXECUTION
// ============================================

// Get command and arguments from terminal
const command = process.argv[2]?.toLowerCase();
const inputPath = process.argv[3];
const outputPath = process.argv[4];

// Validate arguments based on command
if (command === 'help' || command === '--help' || command === '-h' || !command) {
  showHelp();
  process.exit(0);
}

if (command === 'json-to-excel') {
  if (!inputPath || !outputPath) {
    console.error('❌ Error: Missing arguments for json-to-excel');
    console.log('\nUsage: node convert-json-excel.js json-to-excel <input-json> <output-excel>');
    process.exit(1);
  }
  convertJsonToExcel(inputPath, outputPath);
  
} else if (command === 'excel-to-json') {
  if (!inputPath || !outputPath) {
    console.error('❌ Error: Missing arguments for excel-to-json');
    console.log('\nUsage: node convert-json-excel.js excel-to-json <input-excel> <output-json>');
    process.exit(1);
  }
  convertExcelToJson(inputPath, outputPath);
  
} else {
  console.error(`❌ Unknown command: '${command}'`);
  showHelp();
  process.exit(1);
}

```

## How to Use the Optimized Script

1. Install Dependency at root i.e **azzotto-movies**

```
npm install xlsx
```

2. Make It Executable

```
chmod +x convert-json-excel.js

```

3. Convert JSON to Excel (with your paths)

```
node convert-json-excel.js json-to-excel public/data/cycling-ads/cycling-ads.json public/data/spreadsheets/cycling-ads/cycling-ads.xlsx
```

4. Convert Excel back to JSON (after editing)

```
node convert-json-excel.js excel-to-json public/data/spreadsheets/cycling-ads/cycling-ads.xlsx public/data/cycling-ads/cycling-ads.json
```

5. Convert ANY other JSON file

```
node convert-json-excel.js json-to-excel ./any-file.json ./any-output.xlsx

```
