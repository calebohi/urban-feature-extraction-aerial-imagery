# Urban Feature Extraction from Georeferenced Aerial Imagery: Falomo Bridge Area, Lagos

## 📌 Project Overview

This project focuses on the extraction and mapping of selected urban features from a georeferenced aerial image of the Falomo Bridge area in Lagos, Nigeria. The workflow integrates georeferencing, visual interpretation, and vector digitization to derive spatial features including road networks, vegetation cover, and water bodies.

An oblique aerial image was used as the primary data source, requiring careful georeferencing and transformation to align it with real-world coordinates. Following this, key features were manually digitized and styled to produce a clear and interpretable map.

The project demonstrates practical geospatial techniques including image georeferencing, feature extraction, and cartographic visualization, while also addressing limitations associated with perspective distortion and image resampling.

## 🎯 Objectives

- To georeference an oblique aerial image to real-world coordinates  
- To extract key urban features including roads, vegetation, and water bodies using digitization techniques
- To apply visual interpretation and manual digitization techniques  
- To produce a clear and well-structured cartographic output  
- To assess the effects of image distortion and transformation on spatial accuracy

## 📍 Study Area

The study area covers a section of the Falomo Bridge environment in Lagos, Nigeria, characterized by a mix of transportation infrastructure, vegetation, and adjacent water bodies. The area represents a typical urban landscape with significant interaction between built-up features and natural elements.

An oblique (angled) aerial image of the area was used as the primary dataset for this analysis.

### Original Aerial Image

![Original Aerial Image](your-image-link-here)

*Source: iStockphoto (© Kehinde Temitope Odutayo). Used for educational purposes.*

## ⚙️ Methodology

### 📥 Image Acquisition

An oblique (angled) aerial image of the Falomo Bridge area in Lagos was used as the primary dataset for this project. The image was sourced from iStockphoto and selected based on its spatial coverage, visual clarity, and representation of key urban features including roads, vegetation, and water bodies.

Due to its oblique perspective, the image required geometric correction through georeferencing to align it with real-world coordinates before further analysis could be performed.

### 📐 Georeferencing

#### 6.2.1 Georeferencer Setup

The georeferencing process was carried out using the Georeferencer tool in QGIS. This tool was accessed from the top menu via Layer → Georeferencer, which opens a separate interface for performing image-to-map alignment.

To improve workflow efficiency, the Georeferencer window was configured to operate in a docked layout within the main QGIS interface. This was achieved through Settings → Configure Georeferencer → Show georeferencer window docked, allowing the georeferenced image and the reference basemap to be viewed simultaneously.

This setup enabled easier identification and selection of corresponding points between the input image and the reference basemap, thereby improving accuracy during Ground Control Point (GCP) placement.

#### 6.2.2 Image Loading & Workspace Configuration

The aerial image was loaded into the Georeferencer interface as a raster dataset using the Open Raster option. This allowed the image to be displayed within the Georeferencer window for further processing.

To enable accurate spatial alignment, a reference basemap (Google Maps) was added to the main QGIS canvas. The basemap served as the ground reference for identifying real-world positions of features visible in the aerial image.

With the Georeferencer window docked, both the input image and the reference basemap were viewed simultaneously within the same workspace. This configuration facilitated precise selection of corresponding locations during Ground Control Point (GCP) collection, improving the overall georeferencing accuracy.

#### 6.2.3 Transformation Parameters

Prior to georeferencing, transformation parameters were configured within the Georeferencer to ensure accurate alignment and optimal output quality.

A second-order polynomial transformation was selected to account for geometric distortions present in the oblique (angled) aerial image. This method allows for more flexible warping compared to linear transformations, making it suitable for images with perspective-related distortions.

The target Coordinate Reference System (CRS) was set to EPSG:3857 to match the reference basemap, ensuring consistency between the input image and the spatial reference layer.

Multiple resampling methods were evaluated, including nearest neighbour, bilinear, cubic, cubic B-spline, and Lanczos. Among these, cubic B-spline resampling was selected for the final output as it produced the most visually consistent result and significantly reduced the presence of interpolation artifacts, particularly the white pixel distortions observed in vegetated areas.

Additionally, the option to assign a NoData value of 0 was enabled to eliminate black background pixels generated during transformation. Ground Control Point (GCP) data was also saved for reference and reproducibility of the georeferencing process.

#### 6.2.4 Ground Control Point (GCP) Selection

Ground Control Points (GCPs) were collected by identifying distinct and stable features visible in both the aerial image and the reference basemap. Priority was given to features such as road intersections and clearly defined landmarks, which provide reliable positional correspondence.

The Add GCP Point tool in the Georeferencer was used to manually select matching locations between the input image and the basemap. Care was taken to ensure that selected points were well distributed across the image extent to minimize localized distortion and improve overall transformation accuracy.

An iterative approach was adopted during GCP selection, where points were refined and adjusted to reduce positional error. A total of 10 GCPs were used, resulting in a final Root Mean Square (RMS) error of approximately 2.48, which is considered acceptable for georeferencing an oblique (angled) aerial image.

Despite optimization, minor residual distortions remained, particularly towards the upper portion of the image, due to perspective effects inherent in the original imagery.

#### 6.2.5 Transformation & Output Generation

Following the configuration of transformation parameters and selection of Ground Control Points (GCPs), the georeferencing process was executed using the Start Georeferencing function within the Georeferencer tool.

The transformed image was generated as a new georeferenced raster aligned with the reference basemap. The output preserved the spatial relationships defined by the selected GCPs while incorporating the applied transformation and resampling settings.

The resulting raster was successfully integrated into the main QGIS canvas, where it was used as the base layer for subsequent feature extraction and digitization.
