# shinyproxy-base-dockerfiles
Images for deploying shiny apps on the [ShinyProxy](https://github.com/openanalytics/shinyproxy) platform

### Author
Geoffrey Arnold

## Deploying/Using Images

See [docker](https://docs.docker.com/engine/reference/commandline/build/) and [ShinyProxy](https://www.shinyproxy.io/deploying-apps/) documentation.

### Contents
* ipds-shiny-base: Built from [openanalytics/r-base image](https://github.com/openanalytics/r-base). Contains additional R packages and linux packages required for most City of Pittsburgh Shiny app deployments
* ipds-bev-base: Built from shiny-base includes numerous spatial packages (rgdal, leaflet, etc)
* ipds-flexdashboard: No longer maintained, rolled into shiny-base
* ipds-spatial-flexdashboard: No longer maintained, rolled into shiny-base and bev-base
