# Citydao Parcel0 Image Generation and IPFS Process for scripts development

* KML IPFS : ipfs://bafybeieypckzw36w2zolhyttkef6oa2zhuldutljccse66jbakvdxkfyym
* NFT Images IPFS : ipfs://bafybeihyqxva6t4lrsrarkjqptksa6jvaerrynd4nouwh66zqszqzgbeni
* NFT Metadata IPFS : ipfs://bafybeia3lejponr2skhobnhbcoauf4ldvwylpwcqmwgocqx2ustsqx6bby

# Creating Images for Each Plot

## Inputs
1. Tif file of the main plot
2. Geojson containing polygon data of subplots

## Outputs
1. Subplot PNG Images

## Requirements
1. Gdal, Rasterio : Python libraries for tif processing and masking
2. Pyproj, fiona : Python libraries for Coordinate Reference System (CRS) and Conversion
3. Pil : Python library for Image Processing


## Algorithm
1. Parse tif file using Rasterio 
2. Note Coordinate Reference System (CRS) of tif file and render the plot image
3. Parse geojson file 
4. Note Coordinate Reference System (CRS) of geojson file
5. Do CRS tranformation of geojson file to match with tif file
6. Mask individual plot shapes from tif file using rasterio.mask algorithm : https://rasterio.readthedocs.io/en/latest/api/rasterio.mask.html
7. Convert white background into transparent PNG using PIL as rasterio mask fills up image with white background to have a rectanglar image of irregular shapes
8. Draw grid in plot images and resize it 320x320 and 15 px padding on all sides to make it 350x350 which is recommended image size by OpenSea

# IPFS Metadata Generator Script

Have added metedata generator script which parses geojson, and takes input ipfs folder cid of kml and images, and generates jsons for all the plots

# Dividing the Parcel into Plots

## Inputs
1. KML File
2. Number of Parcels

## Outputs
1. Subplots kml and geojson

## Requirements
1. QGIS

## Algorithm
1. Plot Divider Plugin by Dr. Johnny Huck : https://jonnyhuck.co.uk/

