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

#### 1 Georeferencer Setup

The georeferencing process was carried out using the Georeferencer tool in QGIS. This tool was accessed from the top menu via Layer → Georeferencer, which opens a separate interface for performing image-to-map alignment.

To improve workflow efficiency, the Georeferencer window was configured to operate in a docked layout within the main QGIS interface. This was achieved through Settings → Configure Georeferencer → Show georeferencer window docked, allowing the georeferenced image and the reference basemap to be viewed simultaneously.

This setup enabled easier identification and selection of corresponding points between the input image and the reference basemap, thereby improving accuracy during Ground Control Point (GCP) placement.

#### 2 Image Loading & Workspace Configuration

The aerial image was loaded into the Georeferencer interface as a raster dataset using the Open Raster option. This allowed the image to be displayed within the Georeferencer window for further processing.

To enable accurate spatial alignment, a reference basemap (Google Maps) was added to the main QGIS canvas. The basemap served as the ground reference for identifying real-world positions of features visible in the aerial image.

With the Georeferencer window docked, both the input image and the reference basemap were viewed simultaneously within the same workspace. This configuration facilitated precise selection of corresponding locations during Ground Control Point (GCP) collection, improving the overall georeferencing accuracy.

#### 3 Transformation Parameters

Prior to georeferencing, transformation parameters were configured within the Georeferencer to ensure accurate alignment and optimal output quality.

A second-order polynomial transformation was selected to account for geometric distortions present in the oblique (angled) aerial image. This method allows for more flexible warping compared to linear transformations, making it suitable for images with perspective-related distortions.

The target Coordinate Reference System (CRS) was set to EPSG:3857 to match the reference basemap, ensuring consistency between the input image and the spatial reference layer.

Multiple resampling methods were evaluated, including nearest neighbour, bilinear, cubic, cubic B-spline, and Lanczos. Among these, cubic B-spline resampling was selected for the final output as it produced the most visually consistent result and significantly reduced the presence of interpolation artifacts, particularly the white pixel distortions observed in vegetated areas.

Additionally, the option to assign a NoData value of 0 was enabled to eliminate black background pixels generated during transformation. Ground Control Point (GCP) data was also saved for reference and reproducibility of the georeferencing process.

#### 4 Ground Control Point (GCP) Selection

The study area (Falomo Bridge, Lagos) was identified and located on the reference basemap to guide accurate Ground Control Point (GCP) selection.

Ground Control Points (GCPs) were collected by identifying distinct and stable features visible in both the aerial image and the reference basemap. Priority was given to features such as road intersections and clearly defined landmarks, which provide reliable positional correspondence.

The Add GCP Point tool in the Georeferencer was used to manually select matching locations between the input image and the basemap. Care was taken to ensure that selected points were well distributed across the image extent to minimize localized distortion and improve overall transformation accuracy.

An iterative approach was adopted during GCP selection, where points were refined and adjusted to reduce positional error. A total of 10 GCPs were used, resulting in a final Root Mean Square (RMS) error of approximately 2.48, which is considered acceptable for georeferencing an oblique (angled) aerial image.

Despite optimization, minor residual distortions remained, particularly towards the upper portion of the image, due to perspective effects inherent in the original imagery.

#### 5 Transformation & Output Generation

Following the configuration of transformation parameters and selection of Ground Control Points (GCPs), the georeferencing process was executed using the Start Georeferencing function within the Georeferencer tool.

### ✏️ Digitization

Following georeferencing, key urban features were extracted through manual digitization within QGIS. This process involved creating vector layers and interpreting features directly from the georeferenced aerial image.

#### 1 Vector Layer Creation

Separate vector layers were created for each feature class (roads, vegetation, and water bodies) using the GeoPackage format. Layers were created via Layer → Create Layer → New GeoPackage Layer.

The GeoPackage format was selected as it allows multiple feature layers to be stored within a single file, improving data organization and management. For each feature:

- A common database (GeoPackage file) was used  
- Unique table names were assigned (e.g., *roads*, *vegetation*, *water*)  
- Appropriate geometry types were defined:
  - LineString → Roads  
  - Polygon → Vegetation and Water  

This ensured that each feature type was structured correctly for spatial representation.

#### 2 Digitization Workflow

Digitization was performed by enabling editing mode on each layer and manually tracing features from the georeferenced image.

The process involved:

- Activating Toggle Editing to begin feature creation  
- Using appropriate geometry tools based on feature type  
- Carefully tracing visible features to match their real-world shapes  

To improve accuracy and editing efficiency, additional QGIS tools were utilized:

- Snapping tools to ensure proper alignment between connected features  
- Vertex editing tools for refining geometry  
- Advanced digitizing tools to support precise construction and editing  
- Add Ring tool to exclude non-feature areas within polygons (e.g., buildings within vegetation zones)

Digitization required careful visual interpretation of the imagery, particularly in areas affected by distortion or reduced clarity. As such, some features—especially vegetation in the upper portion of the image—were delineated based on best visual approximation.

#### 3 Feature-Specific Considerations

- Roads: Digitized as line features, with dual lines used in areas where physical lane separation (e.g., central dividers) was visible. Road continuity was maintained across intersections and bridge structures.

- Vegetation: Digitized as polygons representing green cover. Inner rings were introduced where necessary to exclude built-up areas within vegetation zones.

- Water Bodies: Digitized as polygons, with feature continuity maintained beneath overlapping infrastructure such as bridges.

#### 4 Data Organization and Styling

Each feature layer was styled independently to enhance map readability. This separation allowed for clear visualization and effective communication of extracted urban features.

## ⚠️ Limitations

While the georeferencing and digitization process produced a usable representation of urban features, several limitations should be acknowledged.

### 1 Oblique Image Distortion

The source aerial image was captured at an oblique (angled) perspective rather than a true vertical (orthographic) view. As a result, perspective distortion was introduced during georeferencing, leading to localized stretching and compression of features—particularly towards the upper portion of the image.

### 2 Residual Georeferencing Error

Although Ground Control Points (GCPs) were carefully selected and refined, the final Root Mean Square (RMS) error of approximately 2.48 indicates the presence of minor positional inaccuracies. This level of error is acceptable for visual interpretation but may not be suitable for high-precision spatial analysis.

### 3 Interpolation Artifacts

Despite the use of cubic B-spline resampling, some minor interpolation artifacts (e.g., pixel inconsistencies within vegetated areas) remained. These artifacts are a result of the transformation process and the original image quality.

### 4 Visual Interpretation Uncertainty

Digitization was based on manual visual interpretation of the imagery. In areas affected by distortion or reduced clarity, particularly towards the upper extent of the image, feature boundaries—especially vegetation—may not accurately represent true ground conditions.

### 5 Limited Feature Scope

Only selected urban features (roads, vegetation, and water bodies) were extracted. Other relevant features such as buildings and infrastructure details were not included, which limits the completeness of the spatial representation.

## 📊 Results

The georeferencing and digitization process resulted in a spatially aligned aerial image with extracted urban features represented as vector layers.

The georeferenced raster was successfully aligned with the reference basemap using a second-order polynomial transformation, achieving a Root Mean Square (RMS) error of approximately 2.48. The use of cubic B-spline resampling improved the visual quality of the output by minimizing interpolation artifacts, particularly in vegetated areas.

Digitization produced three primary feature layers:

- Road Network: Represented as line features, capturing major road alignments and lane separations where visible.  
- Vegetation Cover: Represented as polygon features, delineating green areas with exclusions applied to built-up regions within vegetation zones.  
- Water Bodies: Represented as polygon features, maintaining continuity across areas intersected by infrastructure such as bridges.  

The final map integrates the georeferenced image with the extracted vector features, providing a clear visual representation of urban elements within the study area. The applied symbology enhances feature distinction and supports effective interpretation of spatial patterns.

Overall, the workflow demonstrates the successful application of georeferencing and manual digitization techniques for extracting meaningful spatial information from non-orthogonal aerial imagery.

The transformed image was generated as a new georeferenced raster aligned with the reference basemap. The output preserved the spatial relationships defined by the selected GCPs while incorporating the applied transformation and resampling settings.

The resulting raster was successfully integrated into the main QGIS canvas, where it was used as the base layer for subsequent feature extraction and digitization.

## 🗺️ Map Output

![Final Map](images/final-map.png)

*Final map showing extracted urban features from the georeferenced aerial imagery.*

## 🎯 Conclusion

This project demonstrates the effective application of georeferencing and manual digitization techniques for extracting urban features from aerial imagery. Despite the challenges associated with using an oblique (angled) image, a reasonable level of spatial alignment was achieved through careful Ground Control Point (GCP) selection and appropriate transformation methods.

The workflow highlights the importance of selecting suitable transformation and resampling techniques, as well as the role of visual interpretation in feature extraction. While minor distortions and uncertainties remain, the final output provides a meaningful representation of the study area and its key spatial features.

Overall, this project reinforces the practical value of GIS tools such as QGIS in handling real-world spatial data challenges and producing interpretable cartographic outputs from non-ideal datasets.

## 👤 Author

Ohi  

