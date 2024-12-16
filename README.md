Extreme Winter Storms: Exploring the Impacts of Socioeconomic
Inequalities in a Changing Climate
================

# Contents

This repository contains an analysis of blackout impacts during the
Great Texas Freeze of 2021, evaluating socioeconomic disparities and
spatial patterns of recovery across the Houston metropolitan area.

# Techniques

This repository showcases a range of advanced technical skills and
analytical methodologies, including:

1.  Data Management
    - Wrangling and tidying data using tidyverse, here, and janitor to
      ensure clean, reproducible workflows (Wickham et al. 2019; Müller
      2020; Firke 2023)

    - Visualizations with ggplot2 and tmap (Wickham 2016; Tennekes 2018)

    - Implementation of organized folder structures and detailed
      documentation to facilitate reproducibility and collaborative
      potential

    - Integration of error handling and validation checks to maintain
      data integrity, including conditional statements for spatial and
      statistical consistency

    - Development of generalizable functions to allow for
      reproducibility and flexibility in analyses
2.  Geospatial Analysis
    - Manipulating spatial data with terra and sf, including advanced
      spatial operations such as intersections, raster manipulation, and
      spatial weighting (Hijmans 2024; Pebesma 2018)

    - Creating dynamic and interactive visualizations using tmap to
      explore and communicate geospatial data insights (Tennekes 2018)

    - Leveraging geospatial overlays and zonal statistics to assess the
      relationship between socioeconomic variables and blackout
      classifications

    - Standardizing spatial resolution and alignment across diverse
      datasets to ensure consistency in geospatial analyses
3.  Analysis of Socioeconomic Disparities
    - Integrating census tract-level socioeconomic data to explore
      disparities in blackout status following extreme weather events

    - Employing spatially weighted methods to classify blackout status
      across multiple scales, from individual homes to census tracts

    - Comparing results from different classification approaches (e.g.,
      individual home versus census tract level) to identify
      methodological differences and their implications for
      socioeconomic interpretations

# Data

- The first dataset contains remote sensing images from the [Visible
  Infrared Imaging Radiometer Suite
  (VIIRS)](https://en.wikipedia.org/wiki/Visible_Infrared_Imaging_Radiometer_Suite)
  onboard the Suomi satellite, which captures pre-storm and post-storm
  light intensity changes to evaluate blackout statuses spatially and
  temporally (NASA LAADS DAAC 2023).

<!-- -->

- The second dataset is [Open Street Map
  (OSM)](https://www.openstreetmap.org/#map=4/38.01/-95.84) data for
  home-level resolution, including road networks and infrastructure to
  account for essential services and accessibility (OpenStreetMap
  contributors 2023). This contains two main datasets:
  1.  Roads:
      - Highways account for a large portion of the night lights
        observable from space, so to minimize falsely classifying areas
        that regularly experience reduced traffic levels as having
        experienced a blackout, we will ignore residential buildings
        that are within 200m of highways.
  2.  Homes:
      - The OSM data contains information for all the buildings within
        the area, but we are only interested in considering residential
        buildings since we will be assigning socioeconomic status to
        these features based on census data.

<!-- -->

- The final dataset contains 2019 census tract data collected by the [US
  Census Bureau’s American Community
  Survey](https://www.census.gov/programs-surveys/acs) for the Houston
  metropolis. Census tract geometries were obtained from shapefiles,
  enabling spatial overlays and intersection analyses with blackout
  zones (US Census Bureau 2023).

# Repository Structure

``` bash
      .
      ├── README.md
      ├── README.rmd
      ├── bibs
      │   ├── combined.bib
      │   ├── packages.bib
      │   └── references.bib
      ├── code
      │   ├── custom.css
      │   ├── houston_extreme_storms.html
      │   └── houston_extreme_storms.qmd
      ├── data
      │   ├── ACS_2019_5YR_TRACT_48_TEXAS.gdb
      │   │   ├── a00000001.TablesByName.atx
      │   │   ├── a00000001.gdbindexes
      │   │   ├── a00000001.gdbtable
      │   │   ├── a00000001.gdbtablx
      │   │   └── ...
      │   ├── OSM
      │   │   ├── gis_osm_buildings_a_free_1.gpkg
      │   │   └── gis_osm_roads_free_1.gpkg
      │   └── VNP46A1
      │       ├── VNP46A1.A2021038.h08v05.001.2021039064328.tif
      │       ├── VNP46A1.A2021038.h08v06.001.2021039064329.tif
      │       └── ...
      ├── figures
      │   ├── animations
      │   │   └── nightlight_intensity_animation.gif
      │   ├── density_plots
      │   │   ├── houston_final_density_plot.png
      │   │   └── ...
      │   ├── maps
      │   │   ├── NL_02072021_crop_map.png
      │   │   ├── homes_interactive_map.html
      │   │   ├── lib
      │   │   │   ├── Proj4Leaflet-1.0.1
      │   │   │   │   └── proj4leaflet.js
      │   │   │   └── ...
      │   │   └── tracts_interactive_map.html
      │   └── tables
      │       ├── blackout_summary_kable.html
      │       ├── combined_table_kable.html
      │       └── ...
      ├── houston-storms.Rproj
      └── structure.txt
```

# References

<div id="refs" class="references csl-bib-body hanging-indent"
entry-spacing="0">

<div id="ref-janitor" class="csl-entry">

Firke, Sam. 2023. *Janitor: Simple Tools for Examining and Cleaning
Dirty Data*. <https://CRAN.R-project.org/package=janitor>.

</div>

<div id="ref-terra" class="csl-entry">

Hijmans, Robert J. 2024. *Terra: Spatial Data Analysis*.
<https://CRAN.R-project.org/package=terra>.

</div>

<div id="ref-here" class="csl-entry">

Müller, Kirill. 2020. *Here: A Simpler Way to Find Your Files*.
<https://CRAN.R-project.org/package=here>.

</div>

<div id="ref-viirs_nasa_laads" class="csl-entry">

NASA LAADS DAAC. 2023. “VIIRS: Missions and Measurements.”
<https://ladsweb.modaps.eosdis.nasa.gov/missions-and-measurements/viirs/>.

</div>

<div id="ref-openstreetmap" class="csl-entry">

OpenStreetMap contributors. 2023. “OpenStreetMap.”
<https://www.openstreetmap.org/#map=4/38.01/-95.84>.

</div>

<div id="ref-sf" class="csl-entry">

Pebesma, Edzer. 2018. “<span class="nocase">Simple Features for R:
Standardized Support for Spatial Vector Data</span>.” *The R Journal* 10
(1): 439–46. <https://doi.org/10.32614/RJ-2018-009>.

</div>

<div id="ref-tmap" class="csl-entry">

Tennekes, Martijn. 2018. “<span class="nocase">tmap</span>: Thematic
Maps in R.” *Journal of Statistical Software* 84 (6): 1–39.
<https://doi.org/10.18637/jss.v084.i06>.

</div>

<div id="ref-acs_us_census" class="csl-entry">

US Census Bureau. 2023. “American Community Survey (ACS).”
<https://www.census.gov/programs-surveys/acs>.

</div>

<div id="ref-ggplot2" class="csl-entry">

Wickham, Hadley. 2016. *Ggplot2: Elegant Graphics for Data Analysis*.
Springer-Verlag New York. <https://ggplot2.tidyverse.org>.

</div>

<div id="ref-tidyverse" class="csl-entry">

Wickham, Hadley, Mara Averick, Jennifer Bryan, Winston Chang, Lucy
D’Agostino McGowan, Romain François, Garrett Grolemund, et al. 2019.
“Welcome to the <span class="nocase">tidyverse</span>.” *Journal of Open
Source Software* 4 (43): 1686. <https://doi.org/10.21105/joss.01686>.

</div>

</div>
