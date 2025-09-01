# 🌍 Overpass API Queries for Iraq

This repository contains useful Overpass API queries to extract different kinds of geospatial data for Iraq (area ID 3600304934). You can use these queries with [overpass-api.de](https://overpass-api.de) or any other Overpass API endpoint.

Each section includes the OverpassQL query and a ready-to-run curl snippet.

## 🏔️ Peak Mountains

This query retrieves all geographical features tagged as `"natural"="peak"` within the boundaries of Iraq.

### OverpassQL Query

```overpassql
[out:json][timeout:25];
area(id:3600304934)->.searchArea;
nwr["natural"="peak"](area.searchArea);
out geom;
```

### Ready-to-run curl snippet

```bash
curl -X POST https://overpass-api.de/api/interpreter \
  -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
  --data-urlencode 'data=[out:json][timeout:25];
area(id:3600304934)->.searchArea;
nwr["natural"="peak"](area.searchArea);
out geom;'
```

## 🌱 Global Land Cover

This query is designed to extract a comprehensive range of land cover types, including forests, grasslands, farmlands, and residential areas, from within Iraq.

### OverpassQL Query

```overpassql
[out:json][timeout:60];
area(id:3600304934)->.searchArea;
(
  nwr["natural"="wood"](area.searchArea);
  nwr["landuse"="forest"](area.searchArea);
  nwr["natural"="grassland"](area.searchArea);
  nwr["landuse"="meadow"](area.searchArea);
  nwr["landuse"="farmland"](area.searchArea);
  nwr["natural"="scrub"](area.searchArea);
  nwr["natural"="wetland"](area.searchArea);
  nwr["natural"="desert"](area.searchArea);
  nwr["landuse"="residential"](area.searchArea);
  nwr["landuse"="industrial"](area.searchArea);
  nwr["landcover"](area.searchArea);
)->.landcover;
.landcover out geom;
```

### Ready-to-run curl snippet

```bash
curl -X POST https://overpass-api.de/api/interpreter \
  -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
  --data-urlencode 'data=[out:json][timeout:60];
area(id:3600304934)->.searchArea;
(
  nwr["natural"="wood"](area.searchArea);
  nwr["landuse"="forest"](area.searchArea);
  nwr["natural"="grassland"](area.searchArea);
  nwr["landuse"="meadow"](area.searchArea);
  nwr["landuse"="farmland"](area.searchArea);
  nwr["natural"="scrub"](area.searchArea);
  nwr["natural"="wetland"](area.searchArea);
  nwr["natural"="desert"](area.searchArea);
  nwr["landuse"="residential"](area.searchArea);
  nwr["landuse"="industrial"](area.searchArea);
  nwr["landcover"](area.searchArea);
)->.landcover;
.landcover out geom;'
```

## 💧 Water Bodies & Waterways

This query pulls various water-related features like lakes, rivers, canals, and coastlines found in Iraq.

3A.
### OverpassQL Query

```overpassql
[out:json][timeout:60];
area(id:3600304934)->.searchArea;
(
  nwr["natural"="water"](area.searchArea);
  nwr["water"="lake"](area.searchArea);
  nwr["water"="reservoir"](area.searchArea);
  nwr["landuse"="reservoir"](area.searchArea);
  nwr["natural"="wetland"](area.searchArea);
  nwr["waterway"="river"](area.searchArea);
  nwr["waterway"="stream"](area.searchArea);
  nwr["waterway"="canal"](area.searchArea);
  nwr["waterway"="drain"](area.searchArea);
  nwr["waterway"="ditch"](area.searchArea);
  nwr["natural"="coastline"](area.searchArea);
)->.waterstuff;
.waterstuff out geom;
```

### Ready-to-run curl snippet

```bash
curl -X POST https://overpass-api.de/api/interpreter \
  -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
  --data-urlencode 'data=[out:json][timeout:60];
area(id:3600304934)->.searchArea;
(
  nwr["natural"="water"](area.searchArea);
  nwr["water"="lake"](area.searchArea);
  nwr["water"="reservoir"](area.searchArea);
  nwr["landuse"="reservoir"](area.searchArea);
  nwr["natural"="wetland"](area.searchArea);
  nwr["waterway"="river"](area.searchArea);
  nwr["waterway"="stream"](area.searchArea);
  nwr["waterway"="canal"](area.searchArea);
  nwr["waterway"="drain"](area.searchArea);
  nwr["waterway"="ditch"](area.searchArea);
  nwr["natural"="coastline"](area.searchArea);
)->.waterstuff;
.waterstuff out geom;'
```


3B.
### OverpassQL Query

```overpassql
  [out:json][timeout:60];
  area["ISO3166-1"="IQ"]->.searchArea;
  (
    way["waterway"](area.searchArea);
    relation["waterway"](area.searchArea);
  );
  (
    way["natural"="water"](area.searchArea);
    relation["natural"="water"](area.searchArea);
  );

  out body;
  >;
  out skel qt;
```

### Ready-to-run curl snippet

```bash
curl -X POST https://overpass-api.de/api/interpreter \
  -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
  --data-urlencode 'data=[out:json][timeout:60];
  area["ISO3166-1"="IQ"]->.searchArea;
  (
    way["waterway"](area.searchArea);
    relation["waterway"](area.searchArea);
  );
  (
    way["natural"="water"](area.searchArea);
    relation["natural"="water"](area.searchArea);
  );

  out body;
  >;
  out skel qt;'
```



## 🌳 Parks

This query isolates and returns all areas tagged as `"leisure"="park"` within Iraq.

### OverpassQL Query

```overpassql
[out:json][timeout:60];
area(id:3600304934)->.searchArea;
nwr["leisure"="park"](area.searchArea);
out geom;
```

### Ready-to-run curl snippet

```bash
curl -X POST https://overpass-api.de/api/interpreter \
  -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
  --data-urlencode 'data=[out:json][timeout:60];
area(id:3600304934)->.searchArea;
nwr["leisure"="park"](area.searchArea);
out geom;'
```

## 🚗 Transportation & Buildings

This query retrieves transportation infrastructure and buildings, specifically features with the `"highway"` and `"building"` tags, within Iraq.

### OverpassQL Query

```overpassql
[out:json][timeout:290];
area(id:3600304934)->.searchArea;
(
  nwr["highway"](area.searchArea);
  nwr["building"](area.searchArea);
)->.features;
.features out geom;
```

### Ready-to-run curl snippet

```bash
curl -X POST https://overpass-api.de/api/interpreter \
  -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
  --data-urlencode 'data=[out:json][timeout:290];
area(id:3600304934)->.searchArea;
(
  nwr["highway"](area.searchArea);
  nwr["building"](area.searchArea);
)->.features;
.features out geom;'
```

## Usage

1. Copy any of the OverpassQL queries above and paste them into the [Overpass Turbo](https://overpass-turbo.eu/) web interface
2. Or use the provided curl snippets to run queries directly from your command line
3. The results will be returned in JSON format with geometry data

## Notes

- All queries use Iraq's OpenStreetMap area ID: `3600304934`
- Timeout values are set based on query complexity
- The `out geom;` statement ensures geometry data is included in the results
- For large datasets, consider using smaller bounding boxes or additional filters to reduce response size



# 🌍 Geoapify API Queries for Iraq

## 🏔️ Peak Mountains
```bash
curl "https://api.geoapify.com/v2/places?categories=natural.mountain&filter=rect:37.58482251363806,37.69697510072004,50.935619664490716,27.77968438752873&limit=20&apiKey=3fb279b17d14496ba59c7730ddb78007"
```



## 🌱 Global Land Cover
unfortunately the API does not provide any data about global land cover.



## 💧 Water Bodies & Waterways
```bash
curl "https://api.geoapify.com/v2/places?categories=natural.water&filter=rect:40.17462177333435,36.039997596081136,48.61602771531442,29.7658300395906&limit=20&apiKey=YOUR_API_KEY"
```





## 🌳 Parks
```bash
curl "https://api.geoapify.com/v2/places?categories=entertainment.theme_park,entertainment.water_park,entertainment.activity_park,leisure.park,national_park&filter=rect:39.06596026018283,36.72694808678122,48.50666176751,29.739243146264172&limit=20&apiKey=YOUR_API_KEY"
```





## 🚗 Transportation & Buildings
```bash
curl "https://api.geoapify.com/v2/places?categories=building,public_transport,highway&filter=rect:40.46427679935349,35.34780695837636,46.997736942613265,30.489420049490555&limit=20&apiKey=YOUR_API_KEY"
```


## Notes
- All the data and queries are based on this site [geoapify.com](https://www.geoapify.com) 
- All queries need an api key which should be generated from the source site. click [here](https://myprojects.geoapify.com/login) to get api key
- Many other things can be generated from the api, also it can be more detailed if selected smaller region. for better queries visit this api [playground](https://apidocs.geoapify.com/playground)
