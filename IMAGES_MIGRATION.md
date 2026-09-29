# Image Directory Organization Guide

## Overview
This guide consolidates all image assets from the repository root into a dedicated `images/` directory for better organization and maintainability.

## File Listing
Based on the `Images` file in the root, the following images should be organized:

```
in_layout.jpg
gearbox_fea.png
rollcage_front.jpg
rollcage_isometric.jpg
[and any other image files in the repository]
```

## Migration Steps

### 1. Create the images directory
```bash
mkdir -p images
```

### 2. Move all image files into the new directory
```bash
# Move specific identified images
mv in_layout.jpg images/
mv gearbox_fea.png images/
mv rollcage_front.jpg images/
mv rollcage_isometric.jpg images/

# Or, move all image files at once (from root):
find . -maxdepth 1 -type f \( -iname "*.jpg" -o -iname "*.jpeg" -o -iname "*.png" -o -iname "*.gif" -o -iname "*.webp" -o -iname "*.svg" \) -exec mv {} images/ \;
```

### 3. Update README.md references
Replace all image path references in `README.md`:

**Before:**
```html
<img alt="rollcage_isometric" src="https://github.com/user-attachments/assets/caacf97e-494f-40be-82e0-4c97bfafdf20" />
```

**After (if using local paths):**
```html
<img alt="rollcage_isometric" src="images/rollcage_isometric.jpg" />
```

### 4. Delete the old `Images` root file
```bash
rm Images
```

### 5. Commit changes
```bash
git add images/
git rm Images
git add README.md
git commit -m "refactor: organize images into dedicated directory"
```

## Final Structure
```
repo/
├── README.md
├── LICENSE
├── images/
│   ├── in_layout.jpg
│   ├── gearbox_fea.png
│   ├── rollcage_front.jpg
│   ├── rollcage_isometric.jpg
│   └── [other images]
├── TeamTorque_ATVC2024_DesignPresentation.pptx
├── Copy_of_24172_TeamTorque_Design_Report_1.pdf
└── Prelims_2023-24.pptx
```

## Notes
- The README currently references external GitHub user-attachments URLs for images. Consider downloading and hosting locally if you want full control.
- Keep a `.gitkeep` file in `images/` if it's initially empty to preserve the directory in version control.
- Update the README "Repository Contents" section (line 226-233) to reflect the new structure.
