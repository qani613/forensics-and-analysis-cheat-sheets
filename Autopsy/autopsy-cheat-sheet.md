A cheat sheet for Autopsy, the digital forensics platform, to help you analyze digital evidence:

### Autopsy Basics

- **Opening a Case**:
  - Create/Open a case: `File > New Case` or `File > Open Case`.
  - Add data source: `Case > Add Data Source` to import evidence (disk images, directories, etc.).

### Navigating the Interface

- **Case Dashboard**: Overview of case details, recent activity, and summary.
- **Data Sources**: List of all data sources added to the case.
- **Directory Tree**: Hierarchical view of files and directories in the data source.
- **Results**: Categorized findings like extracted files, keyword hits, and artifacts.
- **Timeline**: Visual representation of events based on timestamps.
- **Views**:
  - **File Metadata**: Shows file properties and metadata.
  - **Content Viewer**: Displays file content (text, hex, strings).
  - **Extracted Content**: Displays extracted data (e.g., EXIF metadata).

### Common Tasks

- **File System Analysis**:
  - Navigate the directory tree to explore files and directories.
  - Right-click on a file/directory for actions: `View File`, `Extract File`, `Add to Report`.

- **Keyword Search**:
  - `Tools > Keyword Search` to search for specific keywords.
  - Add custom keywords or use predefined keyword lists.

- **Hash Analysis**:
  - Calculate and compare file hashes: `Tools > Generate File Hashes`.
  - Import known hash sets for comparison: `Tools > Import Hash Set`.

### Analyzing Artifacts

- **Web Artifacts**:
  - Browse and search web history, cookies, and cache.
  - Found under `Results > Web History`, `Web Cookies`, `Web Downloads`.

- **Email Analysis**:
  - Analyze email files (e.g., PST, MBOX).
  - Found under `Results > Email`.

- **Registry Analysis**:
  - View Windows registry hives and extract key data.
  - Found under `Results > Extracted Registry Values`.

- **Timeline Analysis**:
  - Generate a timeline of file system events: `Tools > Timeline`.
  - Filter by date range, event type, or keyword.

### Reporting

- **Generate Reports**:
  - `Case > Generate Report` to create HTML, Excel, or other report formats.
  - Select data to include: files, keywords, hash sets, etc.

### Useful Shortcuts

- **Case Dashboard**: `Alt + 1`
- **Directory Tree**: `Alt + 2`
- **Results**: `Alt + 3`
- **Timeline**: `Alt + 4`
- **Keyword Search**: `Ctrl + K`
- **Generate Report**: `Ctrl + R`

### Common File Formats

- **Disk Images**: E01, RAW, AFF
- **File Archives**: ZIP, RAR, 7z
- **Email Archives**: PST, MBOX
- **Mobile Data**: Logical and physical dumps

### Customization and Advanced Features

- **Modules**:
  - Install and manage modules: `Tools > Module Manager`.
  - Enable/disable modules based on the investigation needs.

- **Tags and Comments**:
  - Tag files and add comments for future reference.
  - Right-click on a file and select `Tag File` or `Add Comment`.

- **Ingest Jobs**:
  - Configure ingest modules: `Ingest > Configure Ingest Modules`.
  - Select modules like File Type Identification, Keyword Search, etc.

### Example Workflow

1. **Create/Open a Case**:
   - `File > New Case` and fill in case details.
   - Add data source (e.g., disk image).

2. **Initial Analysis**:
   - Browse directory tree for notable files.
   - Perform keyword search for relevant terms.

3. **Artifact Examination**:
   - Check web history and download records.
   - Analyze email archives and registry values.

4. **Timeline Generation**:
   - Create a timeline to understand the sequence of events.
   - Filter by specific dates and events.

5. **Reporting**:
   - Generate a comprehensive report including key findings.
   - Export report in the required format (HTML, Excel).

### Additional Resources

- **Autopsy User Guide**: [Official Documentation](https://www.sleuthkit.org/autopsy/docs/user-docs/4.17.0/)
- **Sleuth Kit and Autopsy Training**: [Training Resources](https://www.sleuthkit.org/training.php)
- **Autopsy Forum**: [Community Support](http://forum.sleuthkit.org/)
