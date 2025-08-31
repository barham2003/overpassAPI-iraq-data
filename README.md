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
