FROM ipds/bev-base

MAINTAINER Geoffrey Arnold "geoffrey.arnold@pittsburghpa.gov"

# install dependencies of FlexDashboard app
RUN R -e "install.packages(c('flexdashboard', 'plotly', 'scales', 'lubridate', 'reshape', 'rlang', 'scales'), repos='https://cloud.r-project.org/')"