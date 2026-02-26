# Nut Cracker

_Author: Alexander Adu-Sarkodie_

JSON-Excel Converter - J2E. Scalable and modular script that accepts input/output paths as terminal arguments. 


## Complete Workflow

- Upload your JSON or Excel file via drag & drop
- Edit input/output paths if needed
- Convert with one click
- Preview the result instantly
- Download or continue editing

**Key Features:**

✅ Fully modular. 

✅ Real server connection status

✅ Drag & drop file upload

✅ File info display (size, modified date)

✅ Live preview after conversion

✅ Auto-refresh file list

✅ Error handling with user feedback

✅ Handles:

- Simple arrays: [{...}, {...}]

- API-style objects: { "movies": [...], "total_results": 12 }

- Single objects: {...} (wraps in array)

- Objects with numeric keys: { "0": {...}, "1": {...} }

✅ Works with any JSON/Excel file - Just specify paths.
 
✅ Auto-creates directories - No need to pre-create folders.
 
✅ Detailed feedback - Shows file sizes, record counts.
 
✅ Error handling - Validates inputs before processing. 

✅ Help system - Built-in documentation.

✅ Scalable - Can be used for any data conversion and processing.

✅ Download Buttons:
Download buttons appear next to JSON and Excel files when they exist

✅ Download button for the last generated file appears in the preview section

✅ Tracks generated files in memory for easy download

✅ Enhanced preview for Excel files showing file info instead of trying to show binary data

✅  Shows file size and name in preview

✅ Server Enhancements: /api/download/:filename endpoint to download generated files and  /api/download-file endpoint to download source files

✅ Responsive design for mobile devices





**Please use with acknowledgement.** Visit:

- **AZZOTTO Movies**,

Free Streaming Service -  https://www.azzottomovies.com/: 

Azzotto Movies is a sophisticated, streaming and entertainment service engineered to cater to a global audience with a specialized focus on regional cinema. The platform demonstrates advanced web development capabilities, featuring a responsive, user-friendly interface built with modern frameworks to ensure a seamless experience across all devices.

Its core functionality is driven by a structured, data-centric architecture, allowing for dynamic content curation and efficient management of a diverse media library. 

Key features include:

**Engagement & Marketing Tools:** Integrated systems like a Newsletter service to build community and drive user retention through direct communication.

**Content Previews:** A dedicated Trailers section to enhance discoverability and fuel user anticipation, acting as a critical marketing funnel within the platform.

**Scalable Infrastructure:** The site is built for performance and scalability, capable of handling media streaming demands and a growing user base without compromising on speed or reliability.

  - _Modules_:
    - https://www.azzottomovies.com/movie/434853
    - https://www.azzottomovies.com/lounge
    - JUKEBOX: Selection of GenXZ music
    - Global Music and Sports Events 2026
    - Pletora of Galleries and Trends

- **SPYDER**

A Net Zero initiative, SPYDER uses  AI-driven analytics and user-friendly compute engine tools to compare tariffs, track consumption, simulate scenarios, predict outcomes, enable forecasting, facilitate predictive maintenance, and recommend cost-effective renewable energy options by saving on energy bills. It integrates dynamic carbon footprint tracking, personalised energy-saving strategies, and compliance frameworks into a scalable platform - helping users align sustainability goals with practical, measurable actions. Its proven track record is honed in applying AI to core business problems. SPYDER uses Machine Learning, Artificial Intelligence, Large Language Models and Retrieve Augmentation Generators algorithms to interpret complex energy tariffs, automating a manual consultancy process and enabling customers to self-serve the best pricing, thereby solving a direct business and customer challenge.

1. https://github.com/kukuu/SPYDER/blob/main/spyder-overview.md
2. https://www.energytariffscheck.com/



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
node convert-json-excel.js json-to-excel public/data/cycling-ads/cycling-ads.json public/data/spreadsheet-json-excel-converter/cycling-ads/cycling-ads.xlsx
```

4. Convert Excel back to JSON (after editing)

```
node convert-json-excel.js excel-to-json public/data/spreadsheet-json-excel-converter/cycling-ads/cycling-ads.xlsx public/data/cycling-ads/cycling-ads.json
```

5. Convert ANY other JSON file

```
node convert-json-excel.js json-to-excel ./any-file.json ./any-output.xlsx

```
## UI J2E Application Converter

https://github.com/kukuu/J2E-Application-Interface/blob/main/README.md  (****PRIVATE**)


<img width="1436" height="731" alt="Screenshot 2026-02-17 at 15 45 52" src="https://github.com/user-attachments/assets/a2e450d9-61d6-481b-9e5f-02a3a1b99f15" />



## JASON Excel Converter - Full-Stack-Solution
⚡ Real-time conversion with backend API 
- https://github.com/kukuu/JSON-Excel-Converter-Full-Stack-Solution (*** **PRIVATE**)

### Snapshots

<img width="1365" height="412" alt="Screenshot 2026-02-26 at 12 07 56" src="https://github.com/user-attachments/assets/a0562884-0bb7-4b4e-8885-d7b58802609b" />

<img width="1362" height="643" alt="Screenshot 2026-02-26 at 12 07 21" src="https://github.com/user-attachments/assets/135cddfe-07dd-4b8f-af4b-c919b429a835" />

<img width="1380" height="231" alt="Screenshot 2026-02-26 at 12 06 56" src="https://github.com/user-attachments/assets/b38cd34e-ccb5-4c3a-afff-950941c65ec8" />
