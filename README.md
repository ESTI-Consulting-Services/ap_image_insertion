# insert_ap_images.py

A Python utility for inserting access point (AP) images into Ekahau AI Pro ESX project files.

## Overview

This script reverses the AP image extraction process used by Francios Verges(https://github.com/francoisverges/semfio-ekahau/blob/master/extract-AP-Images/extract-AP-images.py) by reading AP images from a directory structure and embedding them into Ekahau project files as notes. Each image becomes a separate note attached to the corresponding AP. It also lists inserted images, skipped images and APs without images. 

## Requirements

- Python 3.6+
- Standard library only (no external dependencies)

## Usage

```bash
python insert_ap_images.py SRC_ESX DEST_ESX IMAGES_DIR
```

### Arguments

| Argument | Description |
|----------|-------------|
| `SRC_ESX` | Source Ekahau project file (.esx) |
| `DEST_ESX` | Output Ekahau project file (.esx) |
| `IMAGES_DIR` | Root directory containing AP images |

### Example

```bash
python insert_ap_images.py project.esx project_with_images.esx AP-Images
```

### Options

- `--keep-temp`: Preserve the extracted project directory (useful for debugging)

## Image Directory Structure

```
AP-Images/
├── Floor 1/
│   ├── AP01.png
│   ├── AP01-1.png
│   └── AP02.png
└── Floor 2/
    ├── APName.png
    └── APName-1.png
```

Floor names and AP names must exactly match those defined in the Ekahau project.

## Notes

- You may use the same path for `SRC_ESX` and `DEST_ESX` to overwrite the original project
- Existing notes on APs are preserved; only new notes are added
- Images with unmatched floor or AP names are reported but not inserted
