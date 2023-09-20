# ArcGISPro Export Multiple Maps
This script can be used to export multiple maps from a ArcGIS project layout. This code loops through a list of layer names/group of layers (specified by the user), toggles their visibility in the map, and exports the map layout to a PNG file for each layer/group of layers.

## 1. Prerequisites

- [ArcGIS Desktop](https://www.esri.com/en-us/arcgis/products/arcgis-desktop/overview)
- [Python](https://www.python.org/) (usually comes with ArcGIS installation)

## 2. Important Notes

- This code assumes that the ArcGIS project is currently open and active in the ArcGIS Desktop application.
- Make sure you have the necessary permissions to access the specified export location.

## 3. Step by Step Guide

Follow these steps to execute the code.

1. Open an ArcGISPro project (containing the data and the layout that needed to be exported).

2. Toggle ON the visibility of layers that need to be present in all the exported maps (e.g.: Baselayer). Toggle OFF rest of the layers.

3. Open a Notebook within ArcGISPro. (Insert --> New Notebook)

4. Copy and paste the [script](ArcGISPro_ExportMultipleMaps) into a cell in the Notebook.

5. Run the script. The code will prompt you to enter input variables.
   
6. Enter the input variables. Press <b>'Enter'</b> after entering each input.
   
7. Wait for the code to execute. Then check the output folder.

| Variable name | Description | Example | 
| -------- | -------- | -------- |
| `map_name` | Name of the Map (which contain the spatial layers and linked to the layout) | Map|
| `layout_name` | Name of the Layout (which need to be exported) | Layout1|
| `Layers_list` | To export separate maps for each layer<sup>1</sup>, <br> - Enter list of layer names<sup>2</sup> separated by comma. <br> To export separate maps for each layer group<sup>3</sup>, <br> - Enter list of layer group names separated by comma. <br> | Layer1,Layer2,Layer3 <br> <b>OR</b> <br> Group1,Group2,Group3|
| `Folder_location` | Output folder location for the exported maps | C:\GIS\Test1|
| `File_prefix` | File name prefix for exported maps (Base name) | Map_|
| `File_suffix` | Export with layer/group name (yes/no) | yes <b>OR</b> no|

<sup>1</sup> If layers are organized within groups. Make sure the groups are toggled ON. <br>
<sup>2</sup> Use the name in the content panel (if different from the original name of the shapefile or feature class). <br>
<sup>3</sup> Make sure the layers within the groups are toggled ON. Layers toggled OFF will not be exported with the map.

## 4. Code Explanation

The script performs the following steps:

1. It imports required modules.

2. It opens the current ArcGIS project using the `ArcGISProject` class.

3. The specified map name (`map_name`) and layout name (`layout_name`) is used to obtain a reference to the desired map and layout within the project.

6. The script iterates through each layer/group and toggle their visibility in the map. Then export the map layout to a PNG file.
   
## 5. Features

This code has the following capabilities.
- The `map_name` parameter allows to specify the map within the arcproject.
- The `layout_name` parameter allows to specify the layout you want to export.
- The `Folder_location` parameter allows to change the export Location.
- Both `File_prefix` and `File_suffix` parameters allows to change the output file name.
- Can be used for both vector layers and raster layers.
- Can be used to export separate maps for each layer (Enter a list of layers), group of layers (Enter a list of groups) or a combination.
- Current configuration of the code is to export to png file. To export to any other file type replace 'layout.exportTo<b>PNG</b>' with following,
   - pdf file: 'layout.exportTo<b>PDF</b>'
   - jpeg file: 'layout.exportTo<b>JPEG</b>'

## 6. References
- [ArcGIS Pro Layout Documentation](https://pro.arcgis.com/en/pro-app/latest/arcpy/mapping/layout-class.htm) 


## 7. License

This script is provided under the [MIT License](LICENSE).
