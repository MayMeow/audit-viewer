# audit-viewer

A web-based viewer for Microsoft 365 audit logs with powerful faceted filtering capabilities.

## Features

✨ **Faceted Filter Sidebar**
- Filter audit logs by multiple criteria simultaneously
- Real-time filtering without page reload
- Responsive design - works on desktop and mobile devices
- URL-based filter state (shareable filtered views)

📊 **Large File Support**
- Handles CSV files with hundreds of thousands of rows
- Chunk-based processing for efficient memory usage
- Progressive loading with real-time progress updates

### Filter Types

- **✅ Operation**: Checkbox filters for common operations (FileAccessed, FileModified, FileDeleted, etc.)
- **👤 User**: Searchable user list with autocomplete
- **📄 File Name**: Text search for file names
- **🌐 Site URL**: Text search for SharePoint site URLs
- **🔢 IP Address**: Filter by client IP address
- **📅 Date Range**: Select date range with from/to pickers

## Usage

1. Open `viewer.html` in a modern web browser
2. Click "Choose File" to upload a CSV export of Microsoft 365 audit logs
3. Use the filter sidebar to refine results:
   - Check/uncheck operations
   - Search for specific users, files, or sites
   - Set date ranges
4. View filtered results in real-time
5. Click on "🔍 View" to see detailed AuditData for any record

### Mobile Usage

On mobile devices, tap the "☰ Filters" button in the top-left corner to open the filter sidebar. Tap outside the sidebar or on the overlay to close it.

### Sharing Filtered Views

Filters are automatically saved to the URL. Copy the URL to share a specific filtered view with others.

## CSV Format

The viewer expects CSV files with these columns:
- `CreationDate`: Timestamp of the audit event
- `UserId`: User who performed the action
- `Operation`: Type of operation performed
- `AuditData`: JSON string containing detailed audit information

## Technologies

- [AG-Grid Community](https://www.ag-grid.com/) - Data grid
- [PapaParse](https://www.papaparse.com/) - CSV parsing with chunk-based processing for large files
- Vanilla JavaScript (no build process required)

## Performance

The viewer uses PapaParse's chunk-based parsing to efficiently handle large CSV files:
- No hard limit on file size or row count (previously limited to ~50,000 rows)
- Progressive loading keeps the UI responsive during file processing
- Web Workers offload parsing to a background thread

