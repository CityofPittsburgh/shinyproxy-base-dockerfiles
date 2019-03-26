FROM ipds/shiny-base

MAINTAINER Geoffrey Arnold "geoffrey.arnold@pittsburghpa.gov"

# install dependencies of FlexDashboard app
RUN R -e "install.packages(c('flexdashboard','plotly', 'scales', 'DT', 'zoo', 'lubridate', 'reshape', 'dplyr', 'R4CouchDB'), repos='https://cloud.r-project.org/')"