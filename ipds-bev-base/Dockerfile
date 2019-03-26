FROM ipds/shiny-base

MAINTAINER Geoffrey Arnold "geoffrey.arnold@pittsburghpa.gov"

# system libraries for Burghs Eye View
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
	lbzip2 \
	libfftw3-dev \
	libgdal1-dev \
	libgeos-c1v5 \
	libgsl0-dev \
	libgl1-mesa-dev \
	libglu1-mesa-dev \
	libhdf4-alt-dev \
	libhdf5-dev \
	libnetcdf-dev \
	libsqlite3-dev \
 	tk-dev

RUN apt-get update && apt-get install -y software-properties-common
RUN add-apt-repository ppa:ubuntugis/ubuntugis-unstable

RUN echo "deb http://cran.rstudio.com/bin/linux/ubuntu xenial/  " >> /etc/apt/sources.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9

RUN apt-get update
RUN apt-get upgrade -y

RUN export DEBIAN_FRONTEND=noninteractive; apt-get -y update \
 && apt-get install -y \
	libcurl4-openssl-dev \
	qpdf \
	wget \
	git \
	make \
	libgdal-dev \
	libgeos-dev \
	libproj-dev \
	liblwgeom-dev \
	libudunits2-dev \
	postgis

# stuff for the tmaptools/rmapshaper/geojsonio etc stack:
RUN apt-get install -y libv8-3.14-dev libprotobuf-dev protobuf-compiler libcairo2-dev
RUN add-apt-repository -y ppa:opencpu/jq
RUN apt-get update
RUN apt-get install -y libjq-dev

RUN Rscript -e 'install.packages(c("sf", "lwgeom", "covr", "raster"), dependencies = TRUE, repos = "https://cloud.r-project.org")'
RUN git clone   https://github.com/r-spatial/sf.git
RUN R CMD build --no-build-vignettes sf
RUN R CMD INSTALL sf_*tar.gz

# Prep to install geos
RUN apt-get install -y software-properties-common python-software-properties

RUN add-apt-repository -y ppa:opencpu/jq && \
    apt-get update && \
    apt-get install -y \
        libjq-dev

# system library dependency for the BurghsEyeView app
RUN apt-get update && apt-get install -y \
    binutils \
    libprotobuf-dev \
    libv8-3.14-dev \
    protobuf-compiler

# install dependencies of most BurghsEyeView apps
RUN R -e "install.packages(c('shinythemes', 'jsonlite', 'R4CouchDB', 'leaflet.extras',  'lubridate', 'stringi'), repos='https://cloud.r-project.org/')"