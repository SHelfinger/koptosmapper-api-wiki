# Koptosmapper.de API Wiki

The main maintainer of the API is @SHelfinger (Sebastian Sascha Helfinger)

An API (Application Programming Interface) allows your systems (scripts, programs, database queries, do-files etc.) to interface with our systems in order to extract and process data. 

### Description

The API is fully Restful, takes the form of simple HTTP(s) requests, and returns KML (Keyhole Markup Language) or GeoJSON, having this general format:

`https://geo-data.koptosmapper.de/get.php?param=modul&modul=api&action=load&type=<FORMAT>&load=geo_data&key=<APIKEY>`

The API returns standard KML or GeoJSON objects that can be processed with ease in your script (see examples below).

Currently, available formats are:

Keyhole Markup Language (KML)

`&type=kml`

GeoJSON

`&type=geojson`

### Example

#### KML

`https://geo-data.koptosmapper.de/get.php?param=modul&modul=api&action=load&type=kml&load=geo_data&key=<APIKEY>`

will output each marker from APIKEY Holder in KML format

```kml
<?xml version="1.0" encoding="UTF-8"?>
<kml
	xmlns="http://www.opengis.net/kml/2.2">
	<Schema name="koptosmapper" id="koptosmapper">
		<SimpleField name="unique_id" type="string"/>
		<SimpleField name="KfW Project -&#10;No.(INPRO)" type="float"/>
		<SimpleField name="Project-specific location identifier" type="float"/>
		<SimpleField name="Location name" type="string"/>
		<SimpleField name="Author of the Data&#10;(=the legal owner)" type="string"/>
		<SimpleField name="Publishing restrictions due to security reasons" type="float"/>
		<SimpleField name="Date of data collection or latest update" type="string"/>
		<SimpleField name="Location Activity Status" type="float"/>
		<SimpleField name="Planned or actual start date of activity at the location" type="float"/>
		<SimpleField name="Activity-Description (general)" type="string"/>
		<SimpleField name="Additional Activity-Description" type="string"/>
		<SimpleField name="Location Type IATI" type="string"/>
		<SimpleField name="Alternative Location Type" type="string"/>
		<SimpleField name="DAC 5 Purpose Classification" type="float"/>
		<SimpleField name="Geographic Exactness" type="float"/>
		<SimpleField name="Latitude" type="float"/>
		<SimpleField name="Longitude" type="float"/>
		<SimpleField name="Related Community / Village / Neighborhood" type="string"/>
		<SimpleField name="Additional Geo-data submitted as KML (Lines/Polygons)" type="float"/>
		<SimpleField name="GADM GID" type="string"/>
		<SimpleField name="GID Level" type="string"/>
		<SimpleField name="GADM version" type="string"/>
	</Schema>
	<Folder>
		<name>kooptosmapper</name>
		<Placemark>
			<name>Text</name>
			<ExtendedData>
				<SchemaData schemaUrl="#koptosmapper">
					<SimpleData name="unique_id">ID</SimpleData>
					<SimpleData name="KfW Project - No.(INPRO)">XXXX</SimpleData>
					<SimpleData name="Project-specific location identifier">XXXXX</SimpleData>
					<SimpleData name="Location name">Text</SimpleData>
					<SimpleData name="Author of the Data (=the legal owner)">Author</SimpleData>
					<SimpleData name="Publishing restrictions due to security reasons">(0:1)</SimpleData>
					<SimpleData name="Date of data collection or latest update">2023-03-22</SimpleData>
					<SimpleData name="Location Activity Status">(0-5)</SimpleData>
					<SimpleData name="Planned or actual start date of activity at the location">2018-11-30</SimpleData>
					<SimpleData name="Activity-Description (general)">Text</SimpleData>
					<SimpleData name="Additional Activity-Description">Text</SimpleData>
					<SimpleData name="Location Type IATI">(IATI CODE)</SimpleData>
					<SimpleData name="Alternative Location Type">(IATI CODE)</SimpleData>
					<SimpleData name="DAC 5 Purpose Classification">DAC5</SimpleData>
					<SimpleData name="Geographic Exactness">(0:1)</SimpleData>
					<SimpleData name="Latitude">Float</SimpleData>
					<SimpleData name="Longitude">Float</SimpleData>
					<SimpleData name="Related Community / Village / Neighborhood">Varchar</SimpleData>
					<SimpleData name="Additional Geo-data submitted as KML (Lines/Polygons)">(0:1)</SimpleData>
					<SimpleData name="GADM GID">GID</SimpleData>
					<SimpleData name="GID Level">LEVEL</SimpleData>
					<SimpleData name="GADM version">Version</SimpleData>
				</SchemaData>
			</ExtendedData>
			<Point>
				<coordinates>LNG,LAT</coordinates>
			</Point>
		</Placemark>
		...
	</Folder>
</kml>```

#### GeoJSON

`https://geo-data.koptosmapper.de/get.php?param=modul&modul=api&action=load&type=geojson&load=geo_data&key=<APIKEY>`

will output each marker from APIKEY Holder in GeoJSON format

```json
{
  "type": "FeatureCollection",
  "name": "geo-data",
  "crs": {
    "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
    }
  },
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [
          LNG,
          LAT
        ]
      },
      "properties": {
        "unique_id": "ID",
        "KfW Project - No.(INPRO)": "ID",
        "Project-specific location identifier": "ID",
        "Location name": "Author",
        "Author of the Data (=the legal owner)": "Text",
        "Publishing restrictions due to security reasons": false,
        "Date of data collection or latest update": "DATE",
        "Location Activity Status": "0",
        "Planned or actual start date of activity at the location": "DATE",
        "Additional Activity-Description": "",
        "Location Type IATI": "IATICODE",
        "Alternative Location Type": "IATICODE",
        "DAC 5 Purpose Classification": "DAC5",
        "Geographic Exactness": "0",
        "Latitude": "LAT",
        "Longitude": "LNG",
        "Related Community / Village / Neighborhood": "Text",
        "Additional Geo-data submitted as KML (Lines/Polygons)": 0,
        "GADM GID": "GID",
        "GID Level": "LEVEL",
        "GADM version": "VERSION"
      }
    },
    ...
  ]
}```
