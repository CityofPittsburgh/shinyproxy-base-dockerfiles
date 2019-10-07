FROM cityofpittsburgh/ipds-shiny-base:1.0

MAINTAINER Geoffrey Arnold "geoffrey.arnold@pittsburghpa.gov"

# system libraries for Burghs Eye View
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    lbzip2 \
    libfftw3-dev \
    libgdal-dev \
    libgeos-dev \
    libgsl0-dev \
    libgl1-mesa-dev \
    libglu1-mesa-dev \
    libhdf4-alt-dev \
    libhdf5-dev \
    libjq-dev \
    liblwgeom-dev \
    libpq-dev \
    libproj-dev \
    libprotobuf-dev \
    libnetcdf-dev \
    libsqlite3-dev \
    libssl-dev \
    libudunits2-dev \
    netcdf-bin \
    postgis \
    protobuf-compiler \
    sqlite3 \
    tk-dev \
    unixodbc-dev

# install dependencies of most BurghsEyeView apps
RUN R -e "install.packages(c('shinythemes', 'jsonlite', 'leaflet.extras', 'lubridate', 'stringi', 'devtools', 'postGIStools', 'sf', 'lwgeom', 'raster'), repos='https://cloud.r-project.org/')"

RUN R -e "devtools::install_github('CityofPittsburgh/caRtegraph')"