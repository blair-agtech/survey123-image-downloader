# survey123-image-downloader
Python tool for bulk downloading and organizing Survey123 image attachments with custom filename generation based on survey attributes.

## Overview

This Jupyter notebook automates the process of downloading image attachments from Survey123 surveys and organizing them with custom, descriptive filenames based on survey data attributes. It's particularly useful for field data collection projects where hundreds or thousands of photos need to be extracted and organized systematically.

## Key Features

- **Custom Filename Organization**: Name downloaded images using up to 4 survey attributes (e.g., plot ID, treatment, date) in your preferred order
- **Automatic Filename Cleaning**: Removes verbose descriptive text from Survey123's default filenames while preserving timestamps
- **Preview Mode**: Test filename formatting with a small sample before downloading all attachments
- **Performance Optimized**: 
  - Pre-compiled regex patterns for fast filename processing
  - O(1) dictionary lookups instead of DataFrame filtering
  - Efficient batch processing for large datasets
- **Excel Export**: Automatically exports survey data alongside image downloads
- **CSV Mapping**: Creates reference files linking object IDs to original and renamed filenames
- **Error Handling**: Comprehensive logging and error tracking throughout the download process

## Use Cases

- Agricultural field trials with plot-level photo documentation
- Environmental monitoring surveys with timestamped imagery
- Infrastructure inspections with location-tagged photos
- Any Survey123 project requiring organized bulk image extraction

## Requirements

- Python 3.7+
- ArcGIS API for Python (`arcgis`)
- pandas
- Valid ArcGIS Online or Enterprise credentials
- Access to Survey123 feature service

## Installation

```bash
# Install via conda (recommended)
conda install -c esri arcgis pandas

# Or via pip
pip install arcgis pandas
```

## Quick Start

1. **Open the notebook** in Jupyter Lab/Notebook or VS Code
2. **Configure connection settings** (Section 3):
   - ArcGIS username and password
   - Survey item ID (found in Survey123 URL)
   - Local save path for downloads
3. **Run sections sequentially** to:
   - Connect to your survey
   - Preview available data columns
   - Select attributes for filename generation
   - Test with preview download (2-3 images)
   - Execute full download

## Workflow

### Section 0-1: Setup
Import libraries and configure logging

### Section 2: Performance Optimizations
Pre-compile regex patterns and define utility functions for fast processing

### Section 3: Connect to ArcGIS
Authenticate and retrieve survey feature service

### Section 4: Export Data
Download survey data as Excel and inspect available columns

### Section 5: Filename Cleaning Test
Preview how Survey123's verbose filenames will be cleaned

### Section 6: Select Naming Attributes
Choose up to 4 columns to use in filename generation (order matters!)

### Section 7: Preview Download
Download 2-3 sample images to verify naming scheme

### Section 8: Full Download
Execute bulk download with custom naming and progress tracking

## Example

**Original Survey123 filename:**
```
image_of_plants_in_the_hoop-20250805-173647.jpg
```

**After cleaning + custom attributes:**
```
Plot32_TreatmentA_20250805-173647.jpg
```

## Performance Notes

For large surveys (1000+ images):
- Use short file paths to avoid Windows 260-character limit
- The optimized OID lookup reduces processing time significantly
- Progress updates appear every ~5% completion

## Outputs

- `{survey_name}_data.xlsx`: Full survey data export
- `preview/`: Sample images for testing naming scheme
- `{LayerName}_attachments/`: Organized image folders by layer
- `{LayerName}_attachments.csv`: Mapping files linking object IDs to filenames

## AI-Assisted Development

This tool was developed with AI assistance to accelerate learning and implementation in areas outside my core expertise. AI was used for:
- Initial code structure and ArcGIS API implementation
- Performance optimization recommendations
- Error handling and logging best practices
- Code review and refinement

## License

MIT License - Feel free to use and modify for your projects

## Contributing

Suggestions and improvements welcome! This tool evolved from practical field research needs and continues to be refined based on real-world usage.

## Author

Developed by for agricultural research applications, with a focus on precision agriculture workflows.
