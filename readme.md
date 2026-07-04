# WW2 Tank Battle Map & Unity Terrain Generator

A high-fidelity geospatial tool for visualizing 30 major WWII tank battles and exporting real-world terrain data as 16-bit heightmaps for Unity and Unreal Engine.

## 🛠 Technical Architecture

This application functions as a client-side Geographic Information System (GIS) and terrain-processing pipeline:

* **Mapping Engine:** Powered by **Leaflet.js** for coordinate-accurate placement of historical data.
* **Geospatial Data:** Embedded database of 30 battles across Eastern, Western, North African, Italian, and Pacific fronts, including elevation, combatant stats, and results.
* **Real Elevation Data:** Heightmaps are built from real-world elevation, not a screenshot. The selected area's covering tiles are fetched from AWS's public `elevation-tiles-prod` dataset (Terrarium-encoded, SRTM/GMTED derived), decoded pixel-by-pixel back into meters, and resampled to the chosen resolution — the "Relief/SRTM/Hillshade" layer picker is purely a visual aid for navigating the map and has no effect on the exported terrain.
* **Heightmap Processing:** Real elevation (in meters) is normalized to **16-bit (0-65535)** for professional game engine compatibility. Exported JSON includes the true min/max elevation in meters alongside the normalized data.



## 🚀 Features for Game Developers

* **Real-World Accuracy:** Exported terrain reflects actual elevation data, not a stylized image approximation — flat steppes stay flat, mountains keep their real relief.
* **Area Dimensions:** Real-time calculation of width/height in kilometers and meters.
* **Export Formats:**
    * **PNG:** High-contrast grayscale for visual reference.
    * **RAW:** 16-bit little-endian format for direct Unity Terrain import.
    * **JSON:** Full metadata including GPS coordinates, real min/max elevation in meters, and capture settings.
* **Terrain Filters:** Includes SRTM Elevation and Hillshade layers for varying levels of detail when browsing the map (visual only — see Technical Architecture above).

## 🎮 Unity Import Instructions

1.  **Export:** Select a battlefield, click "Capture Terrain," and download the **RAW** file.
2.  **Unity Setup:** In your Unity Project, create a new **Terrain** object.
3.  **Import:** In Terrain Settings, select **Import Raw**.
4.  **Settings:** * **Depth:** Bit 16.
    * **Byte Order:** Windows (Little Endian).
    * **Dimensions:** Match the resolution (e.g., 512x512 or 1024x1024).

## 📜 Credits & Data
* **Historical Data:** Compiled records of 30 major engagements (1940-1945).
* **Tile Providers:** MapTiler, OpenStreetMap, Esri, and Stadia Maps.
* **Elevation Data:** AWS `elevation-tiles-prod` (Terrarium encoding), sourced from SRTM and GMTED2010.