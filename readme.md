# WW2 Tank Battle Map & Unity Terrain Generator

A high-fidelity geospatial tool for visualizing 30 major WWII tank battles and exporting real-world terrain data as 16-bit heightmaps for Unity and Unreal Engine.

## 🛠 Technical Architecture

This application functions as a client-side Geographic Information System (GIS) and image processing pipeline:

* **Mapping Engine:** Powered by **Leaflet.js** for coordinate-accurate placement of historical data.
* **Geospatial Data:** Embedded database of 30 battles across Eastern, Western, North African, Italian, and Pacific fronts, including elevation, combatant stats, and results.
* **Terrain Capture:** Utilizes **html2canvas** to grab specific map bounds while bypassing road/label overlays for "clean" terrain.
* **Heightmap Processing:** * Converts RGB data to grayscale using the luminosity formula: $0.299R + 0.587G + 0.114B$.
    * Normalizes data to **16-bit (0-65535)** for professional game engine compatibility.



## 🚀 Features for Game Developers

* **Area Dimensions:** Real-time calculation of width/height in kilometers and meters.
* **Export Formats:**
    * **PNG:** High-contrast grayscale for visual reference.
    * **RAW:** 16-bit little-endian format for direct Unity Terrain import.
    * **JSON:** Full metadata including GPS coordinates and capture settings.
* **Terrain Filters:** Includes SRTM Elevation and Hillshade layers for varying levels of detail.

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