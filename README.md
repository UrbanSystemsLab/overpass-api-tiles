# overpass-api-tiles
Mbtiles generator using OSM data from Overpass-API

### Scripts
```
Root
|--osm        # Download directory for .osm files
|--geojson    # Directory for .osm => .geojson files
|--mbtiles    # Directory for (merged .geojson) =>  .mbtile file
|
|--download.js            # Download .osm tiles from Overpass-API
|--download-limit.js      # Do another pass for 0kb .osm tiles (Due to hitting rate limit)
|--osm-to-geojson.js      # convert .osm to .geojson files
\--geojson-merge.js       # Merge .geojson files into single file
```

### Process
- Run `node download.js` to download .osm tiles. The map's bounding box is defined in the script
- The script will hit rate limit couple of times and download 0kb tiles. Run `node download-limit.js` till all tiles have been downloaded.
- Run `node osm-to-geojson.js` to convert .osm to .geojson files
- Run `node geojson-merge.js` to merge .geojson files into single file
- The final output will be a single .mbtile in `\mbtiles` folder

You can serve these tiles using `tileserver-gl-light`


### Tile Downloader Process
Just a visual reference of how sequence of how tiles are downloaded
![tile-download.png](img\tile-download.png)

### TODO
- Combine download.js and download-limit.js
- Accept argument for bounding box parameters
