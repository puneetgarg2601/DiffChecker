# ⚡ Quick Start Guide

## Prerequisites Required

**You need Node.js installed first!**

1. Go to https://nodejs.org/
2. Download **LTS version** (Long Term Support)
3. Run the installer
4. Restart your terminal/PowerShell

## Setup (3 Steps)

### Step 1: Install Dependencies
Open PowerShell in this folder and run:
```powershell
npm install
```

Wait for installation to complete (~2-3 minutes first time).

### Step 2: Test Core Logic (Optional)
Verify the comparison algorithms work:
```powershell
node tests/test-comparator.js
```

You should see:
```
🧪 Testing DiffChecker Core Logic
✅ diff package found
📁 Setting up test data...
✅ Test data created
...
✅ All tests completed!
```

### Step 3: Run the Application
```powershell
npm start
```

The DiffChecker window will open!

## How to Use

### Compare Two Files
1. Click **Browse** next to "Path A"
2. Select a file (e.g., `file1.txt`)
3. Click **Browse** next to "Path B"
4. Select another file (e.g., `file2.txt`)
5. Click **🚀 Compare**
6. View side-by-side differences

### Compare Two Folders
1. Click **Browse** next to "Path A"
2. Select a folder
3. Click **Browse** next to "Path B"
4. Select another folder
5. Click **🚀 Compare**
6. See file tree on the left
7. Click any file to see differences on the right

## Build Executable

Create Windows installer:
```powershell
npm run build
```

Find installer in: `dist/DiffChecker Setup.exe`

## Troubleshooting

### "npm is not recognized"
- Node.js not installed or not in PATH
- Solution: Install Node.js from https://nodejs.org/
- Restart PowerShell after installation

### "Cannot find module 'diff'"
- Dependencies not installed
- Solution: Run `npm install`

### App doesn't open
- Delete `node_modules` folder
- Run `npm install` again
- Run `npm start`

---

**That's it! Happy diffing! 🎉**
