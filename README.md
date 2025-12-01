# VertPrairie-Mapper V2.0
### 🌾 Interactive Grassland Classification WebMap for Quebec Regional Farms

![Version](https://img.shields.io/badge/version-2.0-blue)
![Status](https://img.shields.io/badge/status-active-success)
![License](https://img.shields.io/badge/license-proprietary-red)

**Developed by [Grassland Analytica](https://www.grasslandanalytica.com)**

---

## 📊 Overview

VertPrairie-Mapper V2.0 is a powerful, interactive web mapping platform for visualizing and analyzing grassland management classifications across **2,336 farms** covering **10,326 hectares** in Quebec, Canada.

### Key Features
- 🗺️ **Interactive satellite-based map** with classification overlay
- 🌍 **Bilingual interface** (English/Français)
- ✏️ **Custom area analysis** with drawing tools
- 📈 **Real-time statistics** by classification type
- 📱 **Responsive design** works on desktop and tablet
- 🎨 **Color-coded legend** for easy identification

---

## 🚀 Quick Start

### View Live Demo
👉 **[Launch VertPrairie-Mapper](https://grasslandanalytica.github.io/VertPrairie-Mapper/)** 👈

### Run Locally

**Important:** You must serve the app through a web server (CORS requirement).

```bash
# Clone the repository
git clone https://github.com/GrasslandAnalytica/VertPrairie-Mapper.git
cd VertPrairie-Mapper

# Start local server (choose one)
python3 -m http.server 8000      # Python 3
python -m SimpleHTTPServer 8000  # Python 2
npx http-server -p 8000          # Node.js

# Open in browser
open http://localhost:8000
```

❌ **Do NOT** open `index.html` directly — it will fail due to CORS restrictions.

---

## 📊 Dataset Statistics

| Metric | Value |
|--------|-------|
| **Total Farms** | 2,336 |
| **Total Area** | 10,326 hectares |
| **Data Resolution** | 5 meters |
| **Classification Date** | November 2025 |

### Classification Breakdown

| Class | Description (EN/FR) | Area (ha) | Percentage |
|-------|---------------------|-----------|------------|
| 🟨 **1** | Mechanically harvested (hay) / Prairies récoltées mécaniquement (foin) | 6,339 | 61.4% |
| 🟩 **2** | Intensive grazing / Pâturage intensif | 556 | 5.4% |
| 🟢 **3** | Extensive grazing / Pâturage extensif | 2,195 | 21.3% |
| 🟫 **4** | Fallow / Uncultivated land / Friches | 1,236 | 12.0% |

---

## 🎯 How to Use

### Basic Navigation
- **Pan:** Click and drag
- **Zoom:** Scroll wheel or +/- buttons
- **Info:** Click any colored area for details

### Language Toggle
Click the **FR/EN** button (top-right corner) to switch between English and French.

### Custom Area Analysis
1. Select the **polygon** or **rectangle** tool from the left toolbar
2. Draw your area of interest on the map
3. View instant statistics:
   - Total area in hectares
   - Breakdown by classification class
   - Percentage distribution
4. Edit or delete drawings as needed

### Legend
- Each class is color-coded for easy identification
- Red boundary shows the study area extent
- Statistics panel displays total counts and areas

---

## 📁 Repository Structure

```
VertPrairie-Mapper/
├── index.html              # Main web application (18 KB)
├── classification.geojson  # Classification layer (2.0 MB, optimized)
├── AOI.geojson            # Study area boundary (96 KB)
├── logo-new.png           # Grassland Analytica logo (2.2 MB)
└── README.md              # This file
```

---

## 🛠️ Technical Details

### Technologies
- **[Leaflet.js 1.9.4](https://leafletjs.com/)** — Interactive mapping library
- **[Leaflet.Draw 1.0.4](https://leaflet.github.io/Leaflet.draw/)** — Drawing and editing tools
- **[Turf.js 6.x](https://turfjs.org/)** — Spatial analysis engine
- **ESRI World Imagery** — High-resolution satellite base map
- **Stamen Toner Hybrid** — Map labels overlay

### Data Specifications
- **Coordinate System:** WGS84 (EPSG:4326)
- **Source Resolution:** 5 meters (5m × 5m pixels)
- **Original Raster Size:** 11,879 × 11,181 pixels (132M pixels)
- **Processing:** Raster → Vector conversion with 10m simplification
- **Optimization:** 21 MB → 2.0 MB (90% reduction)

### Browser Compatibility
- ✅ Chrome (recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ⚠️ Requires JavaScript enabled

---

## 🔧 Data Processing Workflow

The V2.0 dataset was created through the following geospatial pipeline:

1. **Source Data:** Quebec Regional Farms shapefile (2,336 farm polygons with classification field)
2. **CRS Standardization:** Reproject to UTM Zone 18N (EPSG:32618)
3. **Rasterization:** Convert vector → 5m raster using GDAL `gdal_rasterize`
4. **Vectorization:** Raster → vector polygons using `gdal_polygonize.py`
5. **Simplification:** Reduce geometry complexity (10m Douglas-Peucker)
6. **Reprojection:** Convert to WGS84 (EPSG:4326) for web compatibility
7. **Optimization:** Compress GeoJSON for fast loading

**Tools Used:** GDAL, QGIS, Python, ogr2ogr

---

## 🌍 Use Cases

### 🌾 Agricultural Management
- Identify different grassland management practices at farm-level
- Plan rotations, grazing schedules, and land use changes
- Monitor trends over time with multi-year datasets

### 🌱 Environmental Assessment
- Evaluate grassland biodiversity potential
- Assess ecosystem services (carbon storage, habitat)
- Support agri-environmental program planning

### 📋 Land Use Planning
- Inform zoning and regional planning decisions
- Support agricultural policy development
- Facilitate stakeholder engagement with visual tools

### 🔬 Research & Education
- Visualize spatial patterns in grassland management
- Generate statistics for academic publications
- Teaching tool for precision agriculture courses

---

## 🐛 Troubleshooting

### Error: "Failed to fetch classification data"
**Cause:** Opening `index.html` directly via `file://` protocol (CORS blocks JSON loading)  
**Solution:** Serve through a web server (see [Quick Start](#-quick-start))

### Map shows blank/gray tiles
**Cause:** No internet connection (base maps require online access)  
**Solution:** Connect to internet and refresh

### Changes not visible after editing code
**Cause:** Browser cache  
**Solution:** Hard refresh
- **Mac:** `Cmd + Shift + R` (Chrome/Firefox) or `Cmd + Option + R` (Safari)
- **Windows:** `Ctrl + F5`

### FR/EN button doesn't work
**Cause:** JavaScript error or browser cache  
**Solution:** 
1. Open browser console (F12) to check for errors
2. Hard refresh the page
3. Ensure the button is visible (top-right corner, blue border)

---

## 📝 Version History

### V2.0 — December 2025
- ✨ **Expanded coverage:** 2,336 farms (10,326 ha) vs. V1.0 single farm (938 ha)
- 🎨 **Enhanced UI:** Larger logo, improved FR/EN toggle positioning
- 🌍 **Better translations:** Refined French text matching official terminology
- 📊 **Statistics panel:** Class names instead of numbers
- 🚀 **Performance:** Optimized 2.0 MB GeoJSON (90% smaller than raw data)
- 🐛 **Bug fixes:** Resolved language toggle, CORS error handling

### V1.0 — November 2025
- 🎉 Initial release with single farm classification
- 🗺️ Basic Leaflet map with drawing tools
- 🌐 Bilingual interface (EN/FR)

---

## 🤝 Contributing

We welcome feedback and contributions! If you'd like to:
- Report bugs or issues
- Suggest new features
- Contribute code improvements
- Request custom datasets

Please open an issue or contact us through our website.

---

## 📧 Support & Contact

**Grassland Analytica**  
🌐 Website: [www.grasslandanalytica.com](https://www.grasslandanalytica.com)  
📧 Contact: Visit website for inquiry form  
💼 Services: Custom GIS, remote sensing, precision agriculture

---

## 📄 License & Citation

**© 2025 Grassland Analytica. All rights reserved.**

This software is proprietary and provided for demonstration purposes. For licensing, redistribution, or commercial use inquiries, please contact Grassland Analytica.

### Suggested Citation
```
Grassland Analytica (2025). VertPrairie-Mapper V2.0: Interactive Grassland 
Classification WebMap for Quebec Regional Farms. Retrieved from 
https://github.com/GrasslandAnalytica/VertPrairie-Mapper
```

---

## 🙏 Acknowledgments

- **ESRI** — Satellite imagery base maps
- **Stamen Design** — Map label tiles
- **OpenStreetMap Contributors** — Geospatial data
- **Leaflet**, **Turf.js**, **Leaflet.Draw** — Open-source mapping libraries

---

## 🔖 Tags

`grassland` `agriculture` `webmap` `gis` `remote-sensing` `leaflet` `quebec` `canada` `precision-agriculture` `land-management` `classification` `geojson` `bilingual`

---

**Built with ❤️ by Grassland Analytica** | **Transforming grassland management with data-driven insights** 🌾
