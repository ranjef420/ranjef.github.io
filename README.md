# Reef's Repo - Kodi Repository

A Kodi add-on repository hosted on GitHub Pages.

## Repository Information

- **Version:** 2.0
- **Kodi File Manager URL:** https://ranjef420.github.io/repository.ranjef420/

## Repository Structure
```
ranjef420/repository.ranjef420/
├── .gitignore
├── README.md
├── _repo_generator.py
├── index.html
└── repo/
    ├── repository.ranjef420/
    │   ├── addon.xml
    │   ├── fanart.jpg
    │   └── icon.png
    └── zips/
        ├── addons.xml
        ├── addons.xml.md5
        └── repository.ranjef420/
            ├── addon.xml
            ├── fanart.jpg
            ├── icon.png
            └── repository.ranjef420-2.0.zip
```

## Installing in Kodi

### Step 1: Add Source to File Manager

1. Open Kodi and go to the home screen
2. Click the **Settings** icon (gear icon)
3. Select **File Manager**
4. Click **Add source** (on the left side)
5. Click **<None>**
6. Type exactly: `https://ranjef420.github.io/repository.ranjef420/`
7. Click **OK**
8. Click the box below "Enter a name for this media source"
9. Type: `Reef's Repo` (or any name you prefer)
10. Click **OK**

### Step 2: Install Repository from Zip

1. Return to Kodi home screen
2. Click **Settings** icon (gear icon)
3. Select **Add-ons**
4. Click **Install from zip file**
   - If you see a warning about unknown sources, click **Settings**, enable **Unknown sources**, click **Yes** on the warning, then go back and click **Install from zip file** again
5. Select **Reef's Repo** (the name you entered in Step 1)
6. Click **repository.ranjef420-2.0.zip**
7. Wait for the notification: "Reef's Repo Add-on installed"

### Step 3: Enable Automatic Updates

1. Go to **Settings** > **Add-ons**
2. Click **My add-ons**
3. Select **Program add-ons** (or wherever Reef's Repo appears)
4. Click **Reef's Repo**
5. Click **Configure** (or the settings icon)
6. Ensure **Auto-update** is set to **On** (this is usually enabled by default)
7. Click **OK**

### Step 4: Verify Automatic Updates System-Wide

1. Go to **Settings** > **System** (or **Settings** > **Player** depending on Kodi version)
2. Click **Add-ons** (in the left menu)
3. Ensure **Updates** is set to **Automatic** (not "Notify" or "Off")
4. This ensures all add-ons from your repository will update automatically

### Step 5: Verify Installation

1. Go to **Settings** > **Add-ons**
2. Click **Install from repository**
3. You should see **Reef's Repo** in the list
4. Click it to browse available add-ons

## Maintaining the Repository

### Adding a New Add-on

1. Open terminal in the repository root folder
2. Add the add-on as a Git submodule:
```bash
   git submodule add https://github.com/username/addon-name repo/addon-name
```
3. Update the add-on and bump its version number in its `addon.xml`
4. Generate repository files:
```bash
   python3 _repo_generator.py
```
5. Review changes:
```bash
   git status
   git diff
```
6. Commit and push:
```bash
   git add .
   git commit -m "Add addon-name version X.X.X"
   git push origin master
```

### Updating an Existing Add-on

1. Navigate to the add-on's submodule directory:
```bash
   cd repo/addon-name
```
2. Update to the latest version and bump version number in `addon.xml`
3. Return to repository root:
```bash
   cd ../..
```
4. Update submodule reference:
```bash
   git submodule update --remote repo/addon-name
```
5. Regenerate repository files:
```bash
   python3 _repo_generator.py
```
6. (Optional) Clean up old zip files:
```bash
   # Manually delete older versions from repo/zips/addon-name/
```
7. Commit and push:
```bash
   git add .
   git commit -m "Update addon-name to version X.X.X"
   git push origin master
```

### GitHub Pages Deployment

Changes pushed to the `master` branch automatically trigger a GitHub Pages deployment. The repository becomes available at:
- **Base URL:** https://ranjef420.github.io/repository.ranjef420/
- **Repository Zip:** https://ranjef420.github.io/repository.ranjef420/repository.ranjef420-2.0.zip

Deployment typically completes within 2-3 minutes. Check deployment status at:
https://github.com/ranjef420/repository.ranjef420/actions

## Technical Details

- **Generator Script:** `_repo_generator.py` (version 5)
- **Supported Kodi Versions:** Krypton, Leia, Matrix, Nexus, and generic
- **Hosting:** GitHub Pages
- **Update Method:** Automatic via GitHub Actions workflow

## Troubleshooting

### Repository Not Updating in Kodi
- Wait 2-3 minutes after pushing changes for GitHub Pages to deploy
- Clear Kodi's cache: Settings > System > Add-ons > Clear cache
- Force update: Settings > Add-ons > My add-ons > Reef's Repo > Update

### Deployment Failures
- Check GitHub Actions: https://github.com/ranjef420/repository.ranjef420/actions
- Common issues:
  - Broken Git submodule references
  - Invalid `addon.xml` files
  - File size exceeding GitHub Pages limits (100MB per file)

## Credits

Repository structure based on [drinfernoo/repository.example](https://github.com/drinfernoo/repository.example)