# shinyproxy-base-dockerfiles
Images for deploying shiny apps on the [ShinyProxy](https://github.com/openanalytics/shinyproxy) platform

### Author
Geoffrey Arnold

## Deploying/Using Images

See [docker](https://docs.docker.com/engine/reference/commandline/build/) and [ShinyProxy](https://www.shinyproxy.io/deploying-apps/) documentation.

### Contents
* docker-cron-base: Built from [rocker/geospatial](https://hub.docker.com/r/rocker/geospatial) Contains most of the packages that will be needed for jobs moved to the GCP for Dataflow
* ipds-shiny-base/Dockerfile: Built from [openanalytics/r-base image](https://github.com/openanalytics/r-base). Contains additional R packages and linux packages required for most City of Pittsburgh Shiny app deployments
* ipds-bev-base/Dockerfile: Built from shiny-base includes numerous spatial packages (rgdal, leaflet, etc)
* ipds-flexdashboard/Dockerfile: No longer maintained, rolled into shiny-base
* ipds-spatial-flexdashboard/Dockerfile: No longer maintained, rolled into shiny-base and bev-base
