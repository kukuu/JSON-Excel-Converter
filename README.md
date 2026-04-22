# The "Nut Cracker" 

Author: Alexander Adu-Sarkodie

_JSON to Excel Converter: Intelligent Data Transformation_   


The **Nut Cracker** is a sophisticated B2B SaaS enterprise-grade data conversion platform that seamlessly transforms complex JSON structures into perfectly formatted Excel spreadsheets and vice versa. What sets it apart is its remarkable **intelligent array detection engine** - unlike basic converters that fail when encountering nested data, Nut Cracker recursively searches through JSON objects to find the most meaningful arrays, prioritizing common API response patterns like "transactions," "results," or "data." This means whether you're working with a simple flat array, a deeply nested API response, or a complex object with numeric keys, the system automatically extracts and flattens the data into a clean, tabular format. The platform features an elegant, real-time web interface with drag-and-drop upload, live preview capabilities, and automatic file download options, making it accessible to both technical and non-technical users alike. 

The system's **versatility and resilience** are demonstrated through its robust path resolution engine that dynamically locates files across multiple directories without hardcoded paths, gracefully falling back to default locations when needed. Notable achievements include its ability to handle over 50MB files, process arrays of any size with intelligent column auto-sizing, and maintain data integrity during conversion through comprehensive error handling and validation. The service includes a sophisticated debugging interface, real-time connection monitoring, and automatic file versioning with timestamped outputs. 
 
Whether deployed in a local development environment or scaled to production, Nut Cracker maintains its performance edge through efficient streaming of large datasets, parallel processing capabilities, and a modular architecture that allows for easy extension. The platform has successfully processed thousands of conversions across various industries, from financial data transformation to media asset management, proving its worth as an indispensable tool in any data professional's arsenal.

## Complete Workflow

- Upload your JSON or Excel file via drag & drop 
- Edit input/output paths if needed
- Convert with one click
- Preview the result instantly
- Download or continue editing

**Key Features:**

✅ Fully modular and scalable - Can be used for any data conversion and processing.. 

✅ Real server connection status

✅ Drag & drop file upload

✅ Detailed file info display (file sizes including  name in preview, record counts, modified date). 

✅ Live preview after conversion

✅ Auto-refresh file list

✅ Error handling with user feedback. Validates inputs before processing. 

✅ Handles:

- Simple arrays: [{...}, {...}]

- API-style objects: { "movies": [...], "total_results": 12 }

- Single objects: {...} (wraps in array)

- Objects with numeric keys: { "0": {...}, "1": {...} }

✅ Works with any JSON/Excel file - Just specify paths.
 
✅ Auto-creates directories - No need to pre-create folders.

✅ Help system - Built-in documentation.

✅ Download Buttons: Download buttons appear next to JSON and Excel files when they exist

✅ Download button for the last generated file appears in the preview section

✅ Tracks generated files in memory for easy download

✅ Enhanced preview for Excel files showing file info instead of trying to show binary data

✅ Server Enhancements: /api/download/:filename endpoint to download generated files and  /api/download-file endpoint to download source files

✅ Responsive design for mobile devices

## How to Use the Script

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
node convert-json-excel.js json-to-excel public/data/ft-transactions/ft-transactions.json public/data/spreadsheet-json-excel-converter/ft-transactions/ft-transactions.xlsx
```

4. Convert Excel back to JSON (after editing)

```
node convert-json-excel.js excel-to-json public/data/spreadsheet-json-excel-converter/ft-transactions/ft-transactions.xlsx public/data/ft-transactions/ft-transactions.json
```

5. Convert ANY other JSON file

```
node convert-json-excel.js json-to-excel ./any-file.json ./any-output.xlsx

```

## Vault

⚡ Real-time conversion with backend API 
- https://github.com/kukuu/JSON-Excel-Converter-Full-Stack-Solution (*** **PRIVATE**)

### Snapshots

<img width="1380" height="231" alt="Screenshot 2026-02-26 at 12 06 56" src="https://github.com/user-attachments/assets/b38cd34e-ccb5-4c3a-afff-950941c65ec8" />

<img width="1362" height="643" alt="Screenshot 2026-02-26 at 12 07 21" src="https://github.com/user-attachments/assets/135cddfe-07dd-4b8f-af4b-c919b429a835" />


<img width="1365" height="412" alt="Screenshot 2026-02-26 at 12 07 56" src="https://github.com/user-attachments/assets/a0562884-0bb7-4b4e-8885-d7b58802609b" />



