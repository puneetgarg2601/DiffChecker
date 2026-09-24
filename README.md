# 🔍 DiffChecker

A desktop application for comparing two files or folders side-by-side with highlighted differences.

## Features

- ✅ **File Comparison**: Compare two individual files directly
- ✅ **Folder Comparison**: Recursively compare two folders
- ✅ **Side-by-Side Diff**: View differences with syntax highlighting
- ✅ **Smart Detection**: 
  - File size check (fast)
  - SHA256 hash verification (accurate)
  - Line-by-line diff for text files
- ✅ **Binary File Support**: Detects and reports binary file differences
- ✅ **100MB Limit**: Skips files larger than 100MB for performance
- ✅ **Filtering**: Filter results by status (different, new, deleted, identical)
- ✅ **Dark Theme**: Easy on the eyes for extended use

## Prerequisites

You need **Node.js** installed. Download from: https://nodejs.org/

Recommended: **Node.js 18.x or later**

## Installation

1. **Open PowerShell or Command Prompt** in this folder

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Run the application:**
   ```bash
   npm start
   ```

## Usage

### File Mode
1. Click **Browse** next to "Path A"
2. Select a file
3. Click **Browse** next to "Path B"
4. Select another file
5. Click **Compare** to see side-by-side differences

### Folder Mode
1. Click **Browse** next to "Path A"
2. Select a folder
3. Click **Browse** next to "Path B"
4. Select another folder
5. Click **Compare**
6. View the file tree on the left
7. Click any file to see differences on the right

### Filters
Use the checkboxes to show/hide:
- ✅ Different - Files with content changes
- ✅ New - Files only in Path B
- ✅ Deleted - Files only in Path A
- ✅ Identical - Files that are the same

## Building Executable

To create a Windows installer:

```bash
npm run build
```

The installer will be created in the `dist/` folder.

### Portable Version

```bash
npm run build:portable
```

## Testing Core Logic

Test the comparison algorithms without the GUI:

```bash
npm run test:core
```

Or directly:
```bash
node tests/test-comparator.js
```

## Project Structure

```
DiffChecker/
├── package.json              # Dependencies & scripts
├── electron-builder.yml      # Build configuration
├── assets/
│   └── icon.ico              # Application icon
├── src/
│   ├── main/
│   │   ├── main.js           # Electron main process
│   │   └── preload.js        # Security bridge
│   ├── renderer/
│   │   ├── index.html        # UI structure
│   │   ├── styles.css        # Dark theme styling
│   │   └── renderer.js       # UI logic
│   └── core/
│       ├── comparator.js     # Main orchestrator
│       ├── folder-walker.js  # Recursive folder walking
│       ├── file-compare.js   # Size → Hash → Diff
│       └── diff-generator.js # Line-by-line diff
├── tests/
│   └── test-comparator.js    # Core logic tests
└── dist/                     # Built executables
```

## Comparison Algorithm

### File Comparison Flow
```
1. Check file sizes
   ├─ Different → Files differ (fast)
   └─ Same → Continue
   
2. Calculate SHA256 hashes
   ├─ Match → Files identical
   └─ Differ → Continue
   
3. Check file type
   ├─ Binary → Report "Binary files differ"
   └─ Text → Generate line-by-line diff
```

### Folder Comparison Flow
```
1. Walk Folder A → Build file tree
2. Walk Folder B → Build file tree
3. Compare trees:
   ├─ Files only in A → "Deleted"
   ├─ Files only in B → "New"
   └─ Files in both → Compare content (above)
4. Generate report
```

## Tech Stack

- **Framework**: Electron 28
- **Diff Library**: `diff` (Myers' O(ND) algorithm)
- **Hash**: Node.js crypto (SHA256)
- **UI**: Vanilla JavaScript, CSS Grid/Flexbox

## Troubleshooting

### "npm is not recognized"
Install Node.js from https://nodejs.org/

### App doesn't start
1. Delete `node_modules` folder
2. Run `npm install` again
3. Run `npm start`

### Comparison is slow
- Large folders (>10,000 files) take time
- Files >100MB are skipped automatically
- Binary files are detected and skipped for diff

## License

MIT License - Feel free to use and modify!

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request
