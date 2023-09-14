Repository containing code for Dissertation for MSc Social and Geographic DataScience for candidate ZJXV1.
NB: we cannot provide the full data used as it is property of Zoopla. If data is necessary, this can be request on behalf of the institution (UCL). Furthermore, this is also applicable for certain code, as it can not directly be shared without confiramtion from HR

additional information regarding code usage is provided in the commit messages of the files

for csv as not in geopandas format need the following code (adapted to csv file used)

current df format and need to be transformed to geopandas format to get the accurate epsg 4326 coordinates. 
The necessary code for this transformation is:

import pandas as pd
import geopandas as gpd
LSOA_gdf = pd.read_csv('Boundaries_raw_LSOA.csv')
LSOA_gdf['geometry'] = gpd.GeoSeries.from_wkt(LSOA_gdf['geometry'])
LSOA_gdf = gpd.GeoDataFrame(LSOA_gdf, geometry='geometry')
LSOA_gdf = LSOA_gdf.set_crs("EPSG:4326")
